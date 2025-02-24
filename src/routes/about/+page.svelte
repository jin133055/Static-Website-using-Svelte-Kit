<script>
    import { slide } from "svelte/transition";
</script>

<style>

.navbar {
        position: fixed;
        top: 0;
        width: 100%;
        background: rgba(0, 0, 50, 0.7);
        padding: 1rem 2rem;
        display: flex;
        justify-content: center;
        gap: 5rem;
        backdrop-filter: blur(10px);
        z-index: 1000;
    }

    .navbar a {
        color: white;
        text-decoration: none;
        font-size: 1rem;
        transition: color 0.3s ease;
    }

    .navbar a:hover {
        color: #FFD700;
    }

    .about-banner {
        position: relative;
        width: 100%;
        height: 400px;
        background: url('/images/about1.jpg') center/cover no-repeat;
        display: flex;
        align-items: center;
        justify-content: center;
        color: white;
        font-size: 2.5rem;
        font-weight: bold;
        text-shadow: 2px 2px 10px rgba(0, 0, 0, 0.5);
    }

    .about-banner::before {
        content: "";
        position: absolute;
        top: 0;
        left: 0;
        width: 100%;
        height: 100%;
        background: rgba(0, 0, 0, 0.5); 
        z-index: 1;
    }

    .about-banner span {
        position: relative;
        z-index: 2;
    }


    .about-section {
        display: flex;
        flex-wrap: wrap;
        padding: 1rem 3rem;
        align-items: center;
        justify-content: center;
        gap: 8rem;
    }

    .about-text h2 {
        font-size: 3rem; 
        color: rgba(0, 0, 50, 0.7); 
        font-weight: bold;
        margin-bottom: 1rem;
    }

    .about-text, .about-image {
        flex: 1;
        min-width: 300px;
    }

    .about-text {
        font-size: 1.2rem;
        color: #333;
        line-height: 1.6;
    }

    .about-image img {
        margin-top: 50px;
        width: 95%;
        border-radius: 12px;
        box-shadow: 0 4px 10px rgba(0, 0, 0, 0.1);
    }
</style>

<div class="navbar">
    <a href="/">Home</a>
    <a href="/speakers">Speakers</a>
    <a href="/schedule">Schedule</a>
    <a href="/sponsors">Sponsors</a>
    <a href="/about">About</a>
    <a href="/contact">Contact</a>
</div>

<div class="about-banner">
    <span>Welcome to Tech Conference 2025</span>
</div>

<div class="about-section">
    <div class="about-text" in:slide={{ duration: 500, x: -100 }}>
        <h2>About the Conference</h2>
        <p>
            Tech Conference 2025 is a premier event bringing together technology
            enthusiasts, industry experts, and innovators from around the world.
            Join us for inspiring keynote speeches, engaging panel discussions,
            and hands-on workshops exploring the future of technology.
        </p>
    </div>
    <div class="about-image" in:slide={{ duration: 500, x: 100 }}>
        <img src="/images/about2.jpg" alt="Tech Conference Audience">
    </div>
</div>
