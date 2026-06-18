/* Oshawa Advance Imaging - interactions */
(function () {
  "use strict";

  // ---- Sticky header shadow ----
  var header = document.querySelector(".site-header");
  if (header) {
    var onScroll = function () {
      header.classList.toggle("scrolled", window.scrollY > 8);
    };
    onScroll();
    window.addEventListener("scroll", onScroll, { passive: true });
  }

  // ---- Mobile nav toggle ----
  var toggle = document.querySelector(".nav-toggle");
  var mobileNav = document.querySelector(".mobile-nav");
  if (toggle && mobileNav) {
    toggle.addEventListener("click", function () {
      var open = mobileNav.classList.toggle("open");
      toggle.setAttribute("aria-expanded", open ? "true" : "false");
      document.body.style.overflow = open ? "hidden" : "";
    });
    mobileNav.querySelectorAll("a").forEach(function (a) {
      a.addEventListener("click", function () {
        mobileNav.classList.remove("open");
        toggle.setAttribute("aria-expanded", "false");
        document.body.style.overflow = "";
      });
    });
  }

  // ---- Reveal on scroll ----
  var reveals = document.querySelectorAll(".reveal");
  if ("IntersectionObserver" in window && reveals.length) {
    var io = new IntersectionObserver(function (entries) {
      entries.forEach(function (e) {
        if (e.isIntersecting) {
          e.target.classList.add("in");
          io.unobserve(e.target);
        }
      });
    }, { threshold: 0.12, rootMargin: "0px 0px -40px 0px" });
    reveals.forEach(function (el) { io.observe(el); });
  } else {
    reveals.forEach(function (el) { el.classList.add("in"); });
  }

  // ---- Animated stat counters ----
  var counters = document.querySelectorAll("[data-count]");
  if ("IntersectionObserver" in window && counters.length) {
    var reduce = window.matchMedia("(prefers-reduced-motion: reduce)").matches;
    var co = new IntersectionObserver(function (entries) {
      entries.forEach(function (e) {
        if (!e.isIntersecting) return;
        var el = e.target;
        var target = parseFloat(el.getAttribute("data-count"));
        var dur = 1400;
        if (reduce) { el.textContent = formatNum(target); co.unobserve(el); return; }
        var start = performance.now();
        function tick(now) {
          var p = Math.min((now - start) / dur, 1);
          var eased = 1 - Math.pow(1 - p, 3);
          el.textContent = formatNum(target * eased);
          if (p < 1) requestAnimationFrame(tick);
          else el.textContent = formatNum(target);
        }
        requestAnimationFrame(tick);
        co.unobserve(el);
      });
    }, { threshold: 0.5 });
    counters.forEach(function (el) { co.observe(el); });
  }
  function formatNum(n) {
    return Number.isInteger(n) ? Math.round(n).toString() : Math.round(n).toString();
  }

  // ---- Smooth-scroll for same-page anchors w/ header offset ----
  document.querySelectorAll('a[href^="#"]').forEach(function (link) {
    link.addEventListener("click", function (ev) {
      var id = link.getAttribute("href");
      if (id.length < 2) return;
      var target = document.querySelector(id);
      if (!target) return;
      ev.preventDefault();
      var headerH = header ? header.offsetHeight : 0;
      var y = target.getBoundingClientRect().top + window.scrollY - headerH - 12;
      window.scrollTo({ top: y, behavior: "smooth" });
    });
  });

  // ---- Contact form: opens a prefilled email to the clinic ----
  var form = document.querySelector("#contactForm");
  if (form) {
    form.addEventListener("submit", function (e) {
      e.preventDefault();
      var get = function (name) {
        var el = form.querySelector('[name="' + name + '"]');
        return el ? (el.value || "").trim() : "";
      };
      var fullName = (get("firstName") + " " + get("lastName")).trim();
      var service = get("service");
      var date = get("date");
      var phone = get("phone");
      var email = get("email");
      var message = get("message");

      var subjectBits = ["Appointment Request"];
      if (fullName) subjectBits.push(fullName);
      if (service) subjectBits.push(service);

      var body = [
        "New appointment request from the website:",
        "",
        "Name: " + (fullName || "(not provided)"),
        "Phone: " + (phone || "(not provided)"),
        "Email: " + (email || "(not provided)"),
        "Preferred service: " + (service || "(not specified)"),
        "Preferred date: " + (date || "(not specified)"),
        "",
        "Message:",
        (message || "(none)"),
        "",
        "Please contact me to confirm my appointment. Thank you."
      ].join("\r\n");

      var mailto = "mailto:info@oshawaadvanceimaging.ca"
        + "?subject=" + encodeURIComponent(subjectBits.join(" - "))
        + "&body=" + encodeURIComponent(body);

      var status = document.querySelector("#formStatus");
      if (status) {
        status.hidden = false;
        status.innerHTML = 'Your email is opening now. If nothing happens, email us directly at <a href="mailto:info@oshawaadvanceimaging.ca">info@oshawaadvanceimaging.ca</a> or call <a href="tel:+19052151815">+1 (905) 215-1815</a>.';
      }
      window.location.href = mailto;
    });
  }

  // ---- Footer year ----
  var yr = document.querySelector("#year");
  if (yr) yr.textContent = new Date().getFullYear();
})();
