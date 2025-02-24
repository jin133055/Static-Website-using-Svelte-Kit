<script>
    import { onMount } from "svelte";
    import { fade, fly } from "svelte/transition";

    let speakers = [
        { name: "Dr. Jane Doe", title: "AI Researcher at OpenAI", image: "/images/speaker1.jpg" },
        { name: "John Smith", title: "CTO of TechCorp", image: "/images/speaker2.jpg" },
        { name: "Emily Johnson", title: "Cybersecurity Expert", image: "/images/speaker3.jpg" },
        { name: "Michael Lee", title: "Blockchain Innovator", image: "/images/speaker4.jpg" },
        { name: "Sophia Carter", title: "Quantum Computing Scientist", image: "/images/speaker5.jpg" },
        { name: "David Kim", title: "CEO of FutureTech", image: "/images/speaker6.jpg" }
    ];

    let eventDate = new Date("2025-06-15T09:00:00").getTime();
    let countdownText = "";

    function updateCountdown() {
        let now = new Date().getTime();
        let timeLeft = eventDate - now;
        let days = Math.floor(timeLeft / (1000 * 60 * 60 * 24));
        let hours = Math.floor((timeLeft % (1000 * 60 * 60 * 24)) / (1000 * 60 * 60));
        let minutes = Math.floor((timeLeft % (1000 * 60 * 60)) / (1000 * 60));
        let seconds = Math.floor((timeLeft % (1000 * 60)) / 1000);
        countdownText = `${days}d ${hours}h ${minutes}m ${seconds}s`;
        if (timeLeft < 0) {
            clearInterval(countdownInterval);
            countdownText = "Event Started!";
        }
    }

    onMount(() => {
        updateCountdown();
        let countdownInterval = setInterval(updateCountdown, 1000);
    });
</script>

<style>
    * {
        margin: 0;
        padding: 0;
        box-sizing: border-box;
        font-family: 'Open Sans', sans-serif;
    }

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

    .hero {
        position: relative;
        height: 100vh;
        background: url('/images/conference.jpg') center/cover no-repeat;
        display: flex;
        align-items: center;
        justify-content: center;
        text-align: center;
        color: white;
        padding: 2rem;
    }

    .overlay {
        position: absolute;
        top: 0;
        left: 0;
        width: 100%;
        height: 100%;
        background: rgba(0, 0, 50, 0.7);
    }

    .hero-content {
        position: relative;
        max-width: auto;
    }

    .hero h1 {
        font-size: 4.5rem;
        font-family: 'Montserrat', sans-serif;
    }

    .hero p{
        font-size: 1.5rem;
    }

    .countdown {
        font-size: 1.7rem;
        margin: 1rem 0;
        color: #FFD700;
    }

    .hero button {
        padding: 14px 28px;
        font-size: 1.4rem;
        border: none;
        border-radius: 50px;
        background: #FFD700;
        color: #003366;
        cursor: pointer;
        transition: all 0.3s ease;
    }

    .hero button:hover {
        background: #008080;
        color: white;
    }

    .keynote-section {
        background: #F5F5F5;
        padding: 4rem 2rem;
        text-align: center;
        overflow: hidden;
    }

    .section-title {
        font-size: 3.5rem;
        font-weight: bold;
        color: #003366;
        text-align: center;
        margin-bottom: 2.5rem;
    }

    .carousel-container {
        display: flex;
        overflow-x: auto;
        scroll-behavior: smooth;
        padding: 1rem;
        gap: 30px;
        scrollbar-width: none;
        justify-content: center;
    }
    .carousel-container::-webkit-scrollbar {
        display: none;
    }

    .speaker-card {
        flex: 0 0 auto;
        width: 300px;
        background: white;
        border-radius: 15px;
        box-shadow: 0 4px 10px rgba(0, 0, 0, 0.1);
        padding: 2rem;
        text-align: center;
        transition: transform 0.3s ease, box-shadow 0.3s ease;
        cursor: pointer;
        position: relative;
    }

    .speaker-card:hover {
        transform: scale(1.1);
        box-shadow: 0 10px 20px rgba(0, 0, 0, 0.2);
    }

    .speaker-img {
        width: 140px;
        height: 140px;
        border-radius: 50%;
        object-fit: cover;
        border: 4px solid #FFD700;
        transition: 0.3s ease-in-out;
        display: block;
        margin: 0 auto 1rem;
    }

    .speaker-card:hover .speaker-img {
        border-color: #008080;
    }

    .speaker-name {
        font-size: 1.4rem;
        font-weight: bold;
        margin-bottom: 0.5rem;
        color: #333333;
    }

    .speaker-title {
        font-size: 1.1rem;
        color: #555;
    }

    .bio {
        display: none;
        font-size: 1rem;
        color: #666;
        margin-top: 0.5rem;
    }

    .speaker-card:hover .bio {
        display: block;
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

<div class="hero">
    <div class="overlay"></div>
    <div class="hero-content">
        <h1>Tech Conference 2025</h1>
        <p>"Shaping the Future of Innovation & Technology"</p>
        <div class="countdown">{countdownText}</div>
        <button on:click={() => alert("Registration coming soon!")}>Register Now</button>
    </div>
</div>

<div class="keynote-section">
    <h2 class="section-title">Keynote Speakers</h2>
    <div class="carousel-container">
        {#each speakers as speaker (speaker.name)}
            <div class="speaker-card" in:fade={{ duration: 400 }} out:fly={{ x: -100, duration: 400 }}>
                <img class="speaker-img" src={speaker.image} alt={speaker.name} />
                <p class="speaker-name">{speaker.name}</p>
                <p class="speaker-title">{speaker.title}</p>
                <p class="bio">{speaker.bio}</p>
            </div>
        {/each}
    </div>
</div>
