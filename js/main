document.addEventListener('DOMContentLoaded', () => {
    
    // 1. Navigation Scroll Effect
    const navbar = document.getElementById('navbar');
    
    const handleScroll = () => {
        if (window.scrollY > 80) {
            navbar.classList.add('scrolled');
        } else {
            navbar.classList.remove('scrolled');
        }
    };
    
    // Initial check and event listener
    handleScroll();
    window.addEventListener('scroll', handleScroll, { passive: true });


    // 2. Mobile Menu Toggle
    const hamburger = document.querySelector('.hamburger');
    const mobileNavOverlay = document.querySelector('.mobile-nav-overlay');
    const mobileLinks = document.querySelectorAll('.mobile-nav-content a');

    const toggleMenu = () => {
        const isActive = mobileNavOverlay.classList.toggle('active');
        hamburger.setAttribute('aria-expanded', isActive);
        
        // Animate hamburger icon
        const bars = hamburger.querySelectorAll('.bar');
        if (isActive) {
            bars[0].style.transform = 'translateY(7px) rotate(45deg)';
            bars[1].style.opacity = '0';
            bars[2].style.transform = 'translateY(-7px) rotate(-45deg)';
            document.body.style.overflow = 'hidden'; // Prevent background scroll
        } else {
            bars[0].style.transform = 'none';
            bars[1].style.opacity = '1';
            bars[2].style.transform = 'none';
            document.body.style.overflow = '';
        }
    };

    hamburger.addEventListener('click', toggleMenu);

    // Close menu when a link is clicked
    mobileLinks.forEach(link => {
        link.addEventListener('click', () => {
            if (mobileNavOverlay.classList.contains('active')) {
                toggleMenu();
            }
        });
    });


    // 3. Intersection Observer for Fade-Up Animations
    const observerOptions = {
        root: null,
        rootMargin: '0px 0px -10% 0px',
        threshold: 0.1
    };

    const fadeUpObserver = new IntersectionObserver((entries, observer) => {
        entries.forEach(entry => {
            if (entry.isIntersecting) {
                entry.target.classList.add('is-visible');
                // Unobserve after animating once to keep performance high
                observer.unobserve(entry.target);
            }
        });
    }, observerOptions);

    const fadeElements = document.querySelectorAll('.fade-up');
    fadeElements.forEach(el => fadeUpObserver.observe(el));

});
