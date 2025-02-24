<script>
    import { fade } from "svelte/transition";
    import { Twitter, Linkedin, Github } from "lucide-svelte"; // Importing icons

    let location = {
        name: "Tech Conference Venue",
        address: "123 Innovation Street, Tech City",
        mapLink: "https://www.google.com/maps/embed?pb=!1m18!1m12!1m3!1d3151.835434509374!2d144.9559283153185!3d-37.81720997975159!2m3!1f0!2f0!3f0!3m2!1i1024!2i768!4f13.1!3m3!1m2!1s0x6ad65d5df1f6d1f9%3A0xf4cdd06e06f8325e!2sMelbourne%20Convention%20and%20Exhibition%20Centre!5e0!3m2!1sen!2sau!4v1614032345678"
    };
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

    .contact-wrapper {
        display: flex;
        justify-content: center;
        align-items: center;
        gap: 2rem;
        max-width: 1000px;
        margin: 6rem auto;
        padding: 2rem;
        background: white;
        box-shadow: 0 4px 10px rgba(0, 0, 0, 0.1);
        border-radius: 12px;
    }

    .contact-container {
        flex: 1;
        text-align: center;
    }

    .contact-title {
        font-size: 2rem;
        color: rgba(0, 0, 50, 0.7);
        font-weight: bold;
        margin-bottom: 1rem;
    }

    .contact-form {
        display: flex;
        flex-direction: column;
        gap: 1rem;
    }

    .contact-form input,
    .contact-form textarea {
        width: 100%;
        padding: 12px;
        font-size: 1rem;
        border: 1px solid #ccc;
        border-radius: 8px;
        box-shadow: 0 2px 5px rgba(0, 0, 0, 0.1);
        transition: 0.3s ease-in-out;
    }

    .contact-form input:focus,
    .contact-form textarea:focus {
        outline: none;
        border-color: rgba(0, 0, 50, 0.7);
        box-shadow: 0 0 10px rgba(0, 0, 50, 0.4);
    }

    .contact-form button {
        background: rgba(0, 0, 50, 0.7);
        color: white;
        padding: 12px;
        font-size: 1rem;
        border: none;
        border-radius: 8px;
        cursor: pointer;
        transition: 0.3s;
    }

    .contact-form button:hover {
        background: rgba(0, 0, 50, 0.9);
    }

    .social-links {
        margin-top: 1.5rem;
        display: flex;
        justify-content: center;
        gap: 1.5rem;
    }

    .social-links a {
        color: rgba(0, 0, 50, 0.7);
        transition: 0.3s;
    }

    .social-links a:hover {
        color: #FFD700;
        transform: scale(1.2);
    }

    /* Map Styles */
    .map-container {
        flex: 1;
        border-radius: 12px;
        overflow: hidden;
        height: 350px;
    }

    .map-container iframe {
        width: 100%;
        height: 100%;
        border: none;
    }

    /* Responsive Design */
    @media (max-width: 768px) {
        .contact-wrapper {
            flex-direction: column;
            padding: 1.5rem;
        }

        .map-container {
            width: 100%;
            height: 300px;
        }
    }
</style>

<!-- Navbar -->
<div class="navbar">
    <a href="/">Home</a>
    <a href="/speakers">Speakers</a>
    <a href="/schedule">Schedule</a>
    <a href="/sponsors">Sponsors</a>
    <a href="/about">About</a>
    <a href="/contact">Contact</a>
</div>

<!-- Contact & Map Section -->
<div class="contact-wrapper" in:fade={{ duration: 500 }}>
    <!-- Contact Form -->
    <div class="contact-container">
        <h2 class="contact-title">Get in Touch</h2>
        <form class="contact-form">
            <input type="text" placeholder="Your Name" required />
            <input type="email" placeholder="Your Email" required />
            <textarea rows="5" placeholder="Your Message" required></textarea>
            <button type="submit">Send Message</button>
        </form>

        <div class="social-links">
            <a href="https://twitter.com" target="_blank">
                <Twitter style="width: 30px; height: 30px;" />
            </a>
            <a href="https://linkedin.com" target="_blank">
                <Linkedin style="width: 30px; height: 30px;" />
            </a>
            <a href="https://github.com" target="_blank">
                <Github style="width: 30px; height: 30px;" />
            </a>
        </div>
    </div>

    <!-- Google Map -->
    <div class="map-container">
        <iframe
            title="Event Location Map"
            src={location.mapLink}
            allowfullscreen=""
            loading="lazy"
            referrerpolicy="no-referrer-when-downgrade"
        ></iframe>
    </div>
</div>
