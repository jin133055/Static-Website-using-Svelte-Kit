    <script>
        import { onMount } from "svelte";
        import { fade } from "svelte/transition";

        let speakers = [
            { name: "Dr. Jane Doe", title: "AI Researcher at OpenAI", image: "/images/speaker1.jpg", bio: "Expert in deep learning and AI ethics." },
            { name: "John Smith", title: "CTO of TechCorp", image: "/images/speaker2.jpg", bio: "Pioneer in cloud computing and enterprise solutions." },
            { name: "Emily Johnson", title: "Cybersecurity Expert", image: "/images/speaker3.jpg", bio: "Specialist in network security and data privacy." },
            { name: "Michael Lee", title: "Blockchain Innovator", image: "/images/speaker4.jpg", bio: "Leading developer in decentralized finance (DeFi)." },
            { name: "Sophia Carter", title: "Quantum Computing Scientist", image: "/images/speaker5.jpg", bio: "Researcher in quantum algorithms and computing." },
            { name: "David Kim", title: "CEO of FutureTech", image: "/images/speaker6.jpg", bio: "Entrepreneur in AI-driven automation." }
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

        .speakers-section {
            padding: 5rem 2rem;
            text-align: center;
            background: #F5F5F5;
        }

        .section-title {
            font-size: 3.5rem;
            font-weight: bold;
            color: rgba(0, 0, 50, 0.7);
            text-align: center;
            margin-bottom: 3rem;
            margin-top: 1rem;
        }

        .speakers-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
            gap: 50px;
            max-width: 1100px;
            margin: 0 auto;
        }

        .speaker-card {
            background: white;
            border-radius: 10px;
            box-shadow: 0 4px 10px rgba(0, 0, 0, 0.1);
            overflow: hidden;
            text-align: center;
            transition: transform 0.3s ease, box-shadow 0.3s ease;
        }

        .speaker-card:hover {
            transform: scale(1.05);
            box-shadow: 0 10px 20px rgba(0, 0, 0, 0.2);
        }

        .speaker-img {
            width: 100%;
            height: 280px;
            object-fit: cover;
        }

        .speaker-info {
            padding: 1.5rem;
        }

        .speaker-name {
            font-size: 1.5rem;
            font-weight: bold;
            color: #333;
            margin-bottom: 0.5rem;
        }

        .speaker-title {
            font-size: 1.2rem;
            color: #555;
            margin-bottom: 0.5rem;
        }

        .bio {
            font-size: 1rem;
            color: #666;
            line-height: 1.5;
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

    <div class="speakers-section">
        <h2 class="section-title">Speakers of the day</h2>
        <div class="speakers-grid">
            {#each speakers as speaker (speaker.name)}
                <div class="speaker-card" in:fade={{ duration: 500 }}>
                    <img class="speaker-img" src={speaker.image} alt={speaker.name} />
                    <div class="speaker-info">
                        <p class="speaker-name">{speaker.name}</p>
                        <p class="speaker-title">{speaker.title}</p>
                        <p class="bio">{speaker.bio}</p>
                    </div>
                </div>
            {/each}
        </div>
    </div>
