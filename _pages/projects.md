---
layout: page
title: Projects
permalink: /projects/
description: ""
nav: true
nav_order: 3
display_categories: ""
horizontal: false
---

<!-- pages/projects.md -->

{% assign project_image = "/assets/img/Heatmap_Figure.png" | relative_url %}
{% assign paper_pdf = "/assets/pdf/Riemannian-Geometry-Financial-Correlation.pdf" | relative_url %}
{% assign code_url = "https://github.com/jordieskarajew" %}

<style>
  /* Hide the default al-folio page title on this page only */
  .post-header {
    display: none;
  }

  .projects-custom {
    width: min(1500px, calc(100vw - 3rem));
    margin-left: 50%;
    transform: translateX(-50%);

    --projects-bg: var(--global-bg-color, #ffffff);
    --projects-card-bg: var(--global-card-bg-color, #ffffff);
    --projects-text: var(--global-text-color, #0a0a0a);
    --projects-muted: var(--global-text-color-light, #555555);
    --projects-subtle: #7a7a7a;
    --projects-accent: var(--global-theme-color, #0b80c7);
    --projects-accent-hover: var(--global-hover-color, #0a6fab);
    --projects-border: var(--global-divider-color, #e7e5e3);
    --projects-border-strong: #d6d4d1;
    --projects-radius: 14px;
    --projects-radius-sm: 8px;

    color: var(--projects-text);
    background: var(--projects-bg);
    margin-top: 0;
  }

  .projects-custom *,
  .projects-custom *::before,
  .projects-custom *::after {
    box-sizing: border-box;
  }

  .projects-custom img,
  .projects-custom svg {
    display: block;
    max-width: 100%;
    height: auto;
  }

  .projects-custom a {
    color: inherit;
    text-decoration: none;
  }

  .projects-custom__inner {
    max-width: none;
    margin-inline: auto;
    padding-inline: clamp(0.5rem, 2vw, 2rem);
  }

  .projects-top-row {
    display: flex;
    align-items: center;
    justify-content: center;
    margin-bottom: 2.25rem;
  }

  .projects-tabs {
    display: flex;
    gap: 0.75rem;
    justify-content: center;
    flex-wrap: wrap;
  }

  .projects-tab {
    padding: 0.55rem 1.1rem;
    border-radius: 8px;
    border: 1px solid var(--projects-border);
    background: var(--projects-card-bg);
    color: var(--projects-muted);
    font-family: inherit;
    font-size: 0.88rem;
    font-weight: 500;
    letter-spacing: 0.005em;
    cursor: pointer;
    transition: color 0.15s ease, background 0.15s ease, border-color 0.15s ease;
  }

  .projects-tab:hover {
    color: var(--projects-text);
    border-color: var(--projects-border-strong);
  }

  .projects-tab[aria-selected="true"] {
    background: color-mix(in srgb, var(--projects-accent) 12%, transparent);
    color: var(--projects-accent);
    border-color: color-mix(in srgb, var(--projects-accent) 35%, var(--projects-border));
  }

  .projects-tab:focus-visible {
    outline: 2px solid var(--projects-accent);
    outline-offset: 2px;
  }

  .projects-panel[hidden] {
    display: none;
  }

  .projects-hero {
    padding-block: 0 clamp(2rem, 5vw, 3.5rem);
  }

  .projects-hero-grid {
    display: grid;
    grid-template-columns: minmax(0, 1.35fr) minmax(320px, 0.65fr);
    gap: clamp(2.5rem, 5vw, 5rem);
    align-items: start;
  }

  .projects-kicker {
    color: var(--projects-accent);
    font-size: 0.95rem;
    font-weight: 500;
    margin-bottom: 0.75rem;
    letter-spacing: 0.005em;
  }

  /* Typography now comes from al-folio's .post-title class */
  .projects-title {
    margin: 0 0 1.25rem;
    color: var(--projects-text);
  }

  /* Typography now comes from al-folio's .desc class */
  .projects-subtitle {
    margin: 0 0 1.75rem;
    color: var(--projects-muted);
  }

  /* Body typography now inherits normal al-folio paragraph styling */
  .projects-description {
    font-family: inherit;
    font-size: inherit;
    font-weight: inherit;
    color: var(--projects-muted);
    max-width: 44em;
    margin: 0 0 2.25rem;
    line-height: 1.65;
  }

  .projects-actions {
    display: flex;
    flex-wrap: wrap;
    gap: 0.75rem;
    align-items: center;
    margin-bottom: 2.5rem;
  }

  .projects-btn {
    display: inline-flex;
    align-items: center;
    gap: 0.5rem;
    padding: 0.7rem 1.15rem;
    border-radius: var(--projects-radius-sm);
    font-size: 0.925rem;
    font-weight: 500;
    transition: all 0.15s ease;
    border: 1px solid transparent;
    white-space: nowrap;
  }

  .projects-btn-primary {
    background: var(--projects-accent);
    color: #ffffff !important;
  }

  .projects-btn-primary:hover {
    background: var(--projects-accent-hover);
    color: #ffffff !important;
    transform: translateY(-1px);
    box-shadow: 0 4px 12px -4px rgba(11, 128, 199, 0.4);
  }

  .projects-btn-outline {
    border-color: var(--projects-border-strong);
    color: var(--projects-text) !important;
    background: var(--projects-card-bg);
  }

  .projects-btn-outline:hover {
    border-color: var(--projects-accent);
    color: var(--projects-accent) !important;
  }

  .projects-meta {
    display: flex;
    flex-wrap: wrap;
    gap: 1.75rem;
    padding-top: 1.5rem;
    border-top: 1px solid var(--projects-border);
    font-size: 0.875rem;
    color: var(--projects-subtle);
  }

  .projects-meta-item {
    display: inline-flex;
    align-items: center;
    gap: 0.5rem;
  }

  .projects-meta-item svg {
    color: var(--projects-subtle);
  }

  .projects-visual {
    width: min(100%, 576px);
    justify-self: center;
    border-radius: var(--projects-radius);
    overflow: hidden;
    background: #0a0a0a;
    box-shadow:
      0 1px 2px rgba(0, 0, 0, 0.04),
      0 10px 40px -12px rgba(0, 0, 0, 0.18);
    aspect-ratio: 4 / 3;
    position: relative;
  }

  .projects-visual img {
    width: 100%;
    height: 100%;
    object-fit: cover;
  }

  .projects-empty-state {
    text-align: center;
    padding-block: clamp(3rem, 8vw, 6rem);
  }

  .projects-empty-state .projects-title {
    margin-bottom: 1rem;
  }

  .projects-empty-state .projects-subtitle {
    margin: 0;
  }

  @media (max-width: 1000px) {
    .projects-hero-grid {
      grid-template-columns: 1fr;
    }

    .projects-visual {
      width: min(100%, 520px);
      margin-inline: auto;
    }
  }

  @media (max-width: 768px) {
    .projects-custom {
      width: min(100%, calc(100vw - 1.5rem));
      margin-top: 0;
    }

    .projects-top-row {
      justify-content: center;
      margin-bottom: 1.75rem;
    }

    .projects-tabs {
      justify-content: center;
    }

    .projects-visual {
      width: min(100%, 504px);
      margin-inline: auto;
    }
  }

  @media (prefers-reduced-motion: no-preference) {
    .projects-panel {
      animation: projects-panel-in 0.35s cubic-bezier(0.2, 0.6, 0.2, 1);
    }

    @keyframes projects-panel-in {
      from {
        opacity: 0;
        transform: translateY(6px);
      }

      to {
        opacity: 1;
        transform: none;
      }
    }

    .projects-reveal {
      opacity: 0;
      transform: translateY(8px);
      animation: projects-reveal 0.6s cubic-bezier(0.2, 0.6, 0.2, 1) forwards;
    }

    .projects-reveal-1 {
      animation-delay: 0.05s;
    }

    .projects-reveal-2 {
      animation-delay: 0.12s;
    }

    .projects-reveal-3 {
      animation-delay: 0.19s;
    }

    .projects-reveal-4 {
      animation-delay: 0.26s;
    }

    @keyframes projects-reveal {
      to {
        opacity: 1;
        transform: none;
      }
    }
  }
</style>

<div class="projects-custom" data-projects-custom>
  <div class="projects-custom__inner">
    <div class="projects-top-row">
      <div class="projects-tabs" role="tablist" aria-label="Projects">
        <button
          class="projects-tab"
          id="tab-riemann"
          role="tab"
          type="button"
          data-project-tab
          data-target="project-riemann"
          aria-selected="true"
          aria-controls="project-riemann"
        >
          Riemannian Geometry
        </button>

        <button
          class="projects-tab"
          id="tab-upcoming"
          role="tab"
          type="button"
          data-project-tab
          data-target="project-upcoming"
          aria-selected="false"
          aria-controls="project-upcoming"
        >
          Upcoming Project
        </button>
      </div>
    </div>
  </div>

  <section
    class="projects-hero projects-panel"
    id="project-riemann"
    role="tabpanel"
    aria-labelledby="tab-riemann"
    data-project-panel
  >
    <div class="projects-custom__inner">
      <div class="projects-hero-grid">
        <div>
          <div class="projects-kicker projects-reveal projects-reveal-1">
            Research Paper
          </div>

          <h1 class="post-title projects-title projects-reveal projects-reveal-2">
            The Riemannian Geometry of Financial Correlation
          </h1>

          <p class="desc projects-subtitle projects-reveal projects-reveal-3">
            Geodesic Distance, Estimation Quality, and the Detection of Systemic Stress
          </p>

          <p class="projects-description projects-reveal projects-reveal-4">
            A mathematical and empirical study of correlation matrices as points on a curved Riemannian manifold. This project investigates whether the affine-invariant geodesic distance on SPD(n) provides a more informative measure of correlation stress than Euclidean and log-Euclidean distances, across multiple estimation methods and out-of-sample tests using large-cap U.S. equities from 2003 to 2023.
          </p>

          <div class="projects-actions projects-reveal projects-reveal-4">
            <a class="projects-btn projects-btn-primary" href="{{ paper_pdf }}">
              <svg
                width="16"
                height="16"
                viewBox="0 0 24 24"
                fill="none"
                aria-hidden="true"
                stroke="currentColor"
                stroke-width="2"
                stroke-linecap="round"
                stroke-linejoin="round"
              >
                <path d="M14 2H6a2 2 0 0 0-2 2v16a2 2 0 0 0 2 2h12a2 2 0 0 0 2-2V8z"/>
                <polyline points="14 2 14 8 20 8"/>
              </svg>
              Read Paper
            </a>

            <a class="projects-btn projects-btn-outline" href="{{ code_url }}">
              <svg
                width="16"
                height="16"
                viewBox="0 0 24 24"
                fill="none"
                aria-hidden="true"
                stroke="currentColor"
                stroke-width="2"
                stroke-linecap="round"
                stroke-linejoin="round"
              >
                <polyline points="16 18 22 12 16 6"/>
                <polyline points="8 6 2 12 8 18"/>
              </svg>
              View Code
            </a>
          </div>

          <div class="projects-meta projects-reveal projects-reveal-4">
            <span class="projects-meta-item">
              <svg
                width="14"
                height="14"
                viewBox="0 0 24 24"
                fill="none"
                aria-hidden="true"
                stroke="currentColor"
                stroke-width="2"
                stroke-linecap="round"
                stroke-linejoin="round"
              >
                <rect width="18" height="18" x="3" y="4" rx="2"/>
                <path d="M16 2v4M8 2v4M3 10h18"/>
              </svg>
              2026
            </span>

            <span class="projects-meta-item">
              <svg
                width="14"
                height="14"
                viewBox="0 0 24 24"
                fill="none"
                aria-hidden="true"
                stroke="currentColor"
                stroke-width="2"
                stroke-linecap="round"
                stroke-linejoin="round"
              >
                <path d="M14 2H6a2 2 0 0 0-2 2v16a2 2 0 0 0 2 2h12a2 2 0 0 0 2-2V8z"/>
                <polyline points="14 2 14 8 20 8"/>
              </svg>
              Research Paper
            </span>
          </div>
        </div>

        <div class="projects-visual projects-reveal projects-reveal-4">
          <img
            src="{{ project_image }}"
            alt="Correlation heatmap for the Riemannian geometry of financial correlation project"
            loading="eager"
          >
        </div>
      </div>
    </div>
  </section>

  <section
    class="projects-hero projects-panel"
    id="project-upcoming"
    role="tabpanel"
    aria-labelledby="tab-upcoming"
    data-project-panel
    hidden
  >
    <div class="projects-custom__inner">
      <div class="projects-empty-state">
        <h1 class="post-title projects-title">Upcoming Project</h1>
        <p class="desc projects-subtitle">Stay tuned.</p>
      </div>
    </div>
  </section>
</div>

<script>
  (function () {
    const root = document.querySelector("[data-projects-custom]");
    if (!root) return;

    const tabs = root.querySelectorAll("[data-project-tab]");
    const panels = root.querySelectorAll("[data-project-panel]");

    function activate(target) {
      tabs.forEach(function (tab) {
        const selected = tab.dataset.target === target;
        tab.setAttribute("aria-selected", selected ? "true" : "false");
        tab.setAttribute("tabindex", selected ? "0" : "-1");
      });

      panels.forEach(function (panel) {
        panel.hidden = panel.id !== target;
      });
    }

    tabs.forEach(function (tab) {
      tab.addEventListener("click", function () {
        activate(tab.dataset.target);
      });

      tab.addEventListener("keydown", function (event) {
        if (event.key !== "ArrowRight" && event.key !== "ArrowLeft") return;

        event.preventDefault();

        const list = Array.from(tabs);
        const index = list.indexOf(tab);

        const next =
          event.key === "ArrowRight"
            ? list[(index + 1) % list.length]
            : list[(index - 1 + list.length) % list.length];

        next.focus();
        activate(next.dataset.target);
      });
    });
  })();
</script>
