class FrostCustomizerEngine {
  constructor(config = {}) {
    this.config = config;
    this.styleTag = null;
    this.init();
  }

  init() {
    this.injectStyleSheet();
    this.applyBrand();
    this.applyFrostToggles();
    this.applyButtonModes();
    this.observeDOM();
  }

  update(newConfig) {
    this.config = { ...this.config, ...newConfig };
    this.applyBrand();
    this.applyFrostToggles();
    this.applyButtonModes();
    this.updateStyleSheet();
  }

  injectStyleSheet() {
    if (!document.getElementById("frost-custom-styles")) {
      this.styleTag = document.createElement("style");
      this.styleTag.id = "frost-custom-styles";
      document.head.appendChild(this.styleTag);
    } else {
      this.styleTag = document.getElementById("frost-custom-styles");
    }
    this.updateStyleSheet();
  }

  updateStyleSheet() {
    const { UI = {}, FONT = {} } = this.config;
    const opacityVal = UI.TRANSPARENCY !== undefined ? Math.max(0, Math.min(100, UI.TRANSPARENCY)) / 100 : 1;

    let fontStyles = "";
    if (FONT.FAMILY) fontStyles += `font-family: ${FONT.FAMILY} !important;`;
    if (FONT.SIZE) fontStyles += `font-size: ${FONT.SIZE} !important;`;
    if (FONT.COLOUR) fontStyles += `color: ${FONT.COLOUR} !important;`;
    if (Array.isArray(FONT.FORMAT)) {
      if (FONT.FORMAT.includes("bold")) fontStyles += "font-weight: 700 !important;";
      if (FONT.FORMAT.includes("italic")) fontStyles += "font-style: italic !important;";
      if (FONT.FORMAT.includes("underline")) fontStyles += "text-decoration: underline !important;";
    }

    if (UI.RAW) {
      this.styleTag.textContent = `
        body, #doquestion-container, #doquestion-container * {
          background-color: transparent !important;
          border-radius: 0px !important;
          box-shadow: none !important;
          ${fontStyles}
        }
        #doquestion-container {
          background: ${UI.BACKGROUND || '#FFFFFF'} !important;
        }
      `;
      return;
    }

    this.styleTag.textContent = `
      body, html {
        background: ${UI.BACKGROUND || 'transparent'} !important;
      }
      #doquestion-container {
        background: ${UI.BACKGROUND || 'transparent'} !important;
      }
      .bg-white, [class*="bg-[#222A35]"], .rounded-\\[20px\\] {
        opacity: ${opacityVal} !important;
      }
      #doquestion-container,
      #doquestion-container p,
      #doquestion-container span,
      #doquestion-container h1,
      #doquestion-container h2,
      #doquestion-container a {
        ${fontStyles}
      }
    `;
  }

  applyBrand() {
    const { BRAND = {} } = this.config;

    if (BRAND.TITLE) {
      document.title = BRAND.TITLE;
    }

    if (BRAND.FAVICON) {
      let icon = document.querySelector("link[rel*='icon']");
      if (!icon) {
        icon = document.createElement("link");
        icon.rel = "shortcut icon";
        document.head.appendChild(icon);
      }
      icon.href = BRAND.FAVICON;
    }

    if (BRAND.LOGO) {
      const logoImages = document.querySelectorAll("#logo img");
      logoImages.forEach((img) => {
        img.src = BRAND.LOGO;
        img.srcset = "";
      });
    }
  }

  applyFrostToggles() {
    const { FROST = {} } = this.config;

    const setVisibility = (selector, isVisible) => {
      const element = document.querySelector(selector);
      if (element) {
        element.style.setProperty("display", isVisible ? "" : "none", "important");
      }
    };

    if (FROST.SHOW_VIDEO !== undefined) setVisibility("#doquestion-question-video", FROST.SHOW_VIDEO);
    if (FROST.SHOW_META_DATA !== undefined) setVisibility("#doquestion-question-title", FROST.SHOW_META_DATA);
    if (FROST.SHOW_DIFFICULTY !== undefined) setVisibility("#doquestion-question-difficulty", FROST.SHOW_DIFFICULTY);
    if (FROST.SHOW_CALCULATOR !== undefined) setVisibility("#doquestion-question-calculator", FROST.SHOW_CALCULATOR);
    if (FROST.SHOW_FEEDBACK !== undefined) setVisibility("#feedback-area", FROST.SHOW_FEEDBACK);
    if (FROST.SHOW_WHITEBOARD !== undefined) setVisibility("#doquestion-whiteboard-trigger", FROST.SHOW_WHITEBOARD);
    if (FROST.SHOW_SCROLL_HINT !== undefined) {
      setVisibility("#doquestion-question-scroll-hint", FROST.SHOW_SCROLL_HINT);
      setVisibility("#doquestion-response-scroll-hint", FROST.SHOW_SCROLL_HINT);
    }
    if (FROST.SHOW_NAV_BAR !== undefined) {
      const nav = document.querySelector(".h-16.flex.items-center.justify-between");
      if (nav) nav.style.setProperty("display", FROST.SHOW_NAV_BAR ? "flex" : "none", "important");
    }
  }

  applyButtonModes() {
    const { UI = {} } = this.config;
    const buttons = document.querySelectorAll(
      ".doquestion-response-button, input[type='submit'], #doquestion-question-video, #continuelater-button, #nextquestion-button"
    );

    buttons.forEach((btn) => {
      const icons = btn.querySelectorAll("img, svg");
      
      if (UI.ICONONLY) {
        icons.forEach(i => i.style.display = "inline-block");
        btn.childNodes.forEach((node) => {
          if (node.nodeType === Node.TEXT_NODE) node.textContent = "";
        });
      } else if (UI.TEXTONLY) {
        icons.forEach(i => i.style.display = "none");
      }
    });
  }

  getState() {
    const progressLabel = document.querySelector("#doquestion-progress-label");
    const progressBar = document.querySelector("#doquestion-progress-bar");
    const qListItems = document.querySelectorAll("#doquestion-qnums li");
    const correctNode = document.querySelector("#doquestion-correctanswer");
    const responseH1 = document.querySelector("#doquestion-response h1");

    const answersMap = [];
    qListItems.forEach((li) => {
      answersMap.push({
        id: li.id,
        label: li.querySelector("span")?.innerText?.trim(),
        status: li.classList.contains("correct") ? "correct" : 
                li.classList.contains("incorrect") ? "incorrect" : 
                li.classList.contains("current") ? "current" : "unvisited"
      });
    });

    return {
      progressPercentage: progressLabel ? progressLabel.innerText.trim() : null,
      progressBarWidth: progressBar ? progressBar.style.width : null,
      questions: answersMap,
      resultState: responseH1 ? (responseH1.classList.contains("correct") ? "CORRECT" : "INCORRECT") : null,
      revealedAnswerMML: correctNode ? correctNode.innerHTML : null
    };
  }

  observeDOM() {
    const targetNode = document.getElementById("doquestion-container") || document.body;
    const observer = new MutationObserver(() => {
      this.applyFrostToggles();
      this.applyButtonModes();
      this.applyBrand();
    });

    observer.observe(targetNode, {
      childList: true,
      subtree: true
    });
  }
}

window.FrostAPI = FrostCustomizerEngine;
