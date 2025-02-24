<script>
let sponsors = [
    { name: "Uber", logo: "/images/sponsor1.png", link: "https://www.uber.com/in/en/" },
    { name: "Revolut", logo: "/images/sponsor2.png", link: "https://www.revolut.com" },
    { name: "Adyen", logo: "/images/sponsor3.png", link: "https://www.adyen.com" },
    { name: "WHOOP", logo: "/images/sponsor4.png", link: "https://www.whoop.com" },
    { name: "Cloudflare", logo: "/images/sponsor5.png", link: "https://www.cloudflare.com" },
    { name: "GitLab", logo: "/images/sponsor6.jpg", link: "https://about.gitlab.com" },
    { name: "Stripe", logo: "/images/sponsor7.png", link: "https://stripe.com" },
    { name: "UiPath", logo: "/images/sponsor8.png", link: "https://www.uipath.com" },
    { name: "Rappi", logo: "/images/sponsor9.png", link: "https://www.rappi.com" },
    { name: "Twilio", logo: "/images/sponsor10.png", link: "https://www.twilio.com" },
    { name: "OnePlus", logo: "/images/sponsor11.png", link: "https://www.oneplus.com" },
    { name: "Twitter", logo: "/images/sponsor12.png", link: "https://twitter.com" },
    { name: "Datadog", logo: "/images/sponsor13.webp", link: "https://www.datadoghq.com" },
    { name: "Wayve", logo: "/images/sponsor14.png", link: "https://wayve.ai" },
    { name: "Canva", logo: "/images/sponsor15.png", link: "https://www.canva.com" }
];

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

    .section-title{
        margin: 0.3em;
    }
    .sponsors-section {
        padding: 4rem 2rem;
        text-align: center;
        background: #F5F5F5;
    }

    .section-title {
        font-size: 3.5rem;
        font-weight: bold;
        color: rgba(0, 0, 50, 0.7);
        margin-bottom: 2rem;
    }

    .sponsor-grid {
        display: grid;
        grid-template-columns: repeat(auto-fit, minmax(150px, 1fr));
        gap: 2rem;
        justify-items: center;
        max-width: 1000px;
        margin: 0 auto;
    }

    .sponsor-card {
        display: flex;
        align-items: center;
        justify-content: center;
        background: white;
        border-radius: 12px;
        box-shadow: 0 4px 10px rgba(0, 0, 0, 0.1);
        padding: 20px;
        transition: transform 0.3s ease, box-shadow 0.3s ease;
        width: 100%;
        height: 100px;
    }

    .sponsor-card:hover {
        transform: scale(1.1);
        box-shadow: 0 10px 20px rgba(0, 0, 0, 0.2);
    }

    .sponsor-logo {
        max-width: 100%;
        max-height: 80px;
        object-fit: contain;
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

<div class="sponsors-section">
    <h2 class="section-title">Our Sponsors</h2>

    <div class="sponsor-grid">
        {#each sponsors as sponsor}
            <a href={sponsor.link} target="_blank" rel="noopener noreferrer" class="sponsor-card">
                <img class="sponsor-logo" src={sponsor.logo} alt={sponsor.name} />
            </a>
        {/each}
    </div>
</div>
