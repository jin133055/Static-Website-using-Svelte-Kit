<script>
    import { fly } from "svelte/transition";

    let selectedDay = "March 10, 2025"; // Default to first day

    let schedule = [
        { date: "March 10, 2025", time: "09:00 AM - 10:00 AM", topic: "Opening Keynote: The Future of AI", speaker: "Dr. Jane Doe", link: "/speakers/jane-doe" },
        { date: "March 10, 2025", time: "10:30 AM - 11:30 AM", topic: "Cybersecurity in the Age of AI", speaker: "Emily Johnson", link: "/speakers/emily-johnson" },
        { date: "March 10, 2025", time: "01:00 PM - 02:00 PM", topic: "Blockchain and Decentralized Finance", speaker: "Michael Lee", link: "/speakers/michael-lee" },
        { date: "March 10, 2025", time: "03:00 PM - 04:00 PM", topic: "Quantum Computing Advances", speaker: "Sophia Carter", link: "/speakers/sophia-carter" },
        { date: "March 11, 2025", time: "09:00 AM - 10:00 AM", topic: "Cloud Computing Trends", speaker: "John Smith", link: "/speakers/john-smith" },
        { date: "March 11, 2025", time: "11:00 AM - 12:00 PM", topic: "AI and Automation in Industry", speaker: "David Kim", link: "/speakers/david-kim" }
    ];

    // Filter sessions based on selected day
    $: filteredSchedule = schedule.filter(session => session.date === selectedDay);

    function changeDay(day) {
        selectedDay = day;
    }
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

    .schedule-section {
        padding: 5rem 2rem;
        text-align: center;
        background: #F5F5F5;
    }

    .section-title {
        font-size: 3.5rem;
        font-weight: bold;
        color: rgba(0, 0, 50, 0.7);
        margin-bottom: 1rem;
    }

    .tabs {
        display: flex;
        justify-content: center;
        gap: 1rem;
        margin-bottom: 2rem;
    }

    .tab-button {
        padding: 10px 20px;
        font-size: 1.2rem;
        font-weight: bold;
        border: none;
        background: #ccc;
        cursor: pointer;
        transition: background 0.3s ease;
        border-radius: 8px;
    }

    .tab-button.active {
        background: rgba(0, 0, 50, 0.7);
        color: white;
    }

    .tab-button:hover {
        background: #d1b61e;
        color: white;
    }

    .schedule-table {
        width: 100%;
        max-width: 1000px;
        margin: 0 auto;
        border-collapse: collapse;
        font-size: 1.2rem;
    }

    .schedule-table th, .schedule-table td {
        padding: 15px;
        border: 1px solid #ccc;
        text-align: left;
    }

    .schedule-table th {
        background: rgba(0, 0, 50, 0.7);
        color: white;
    }

    .schedule-table tr:nth-child(even) {
        background: #E8E8E8;
    }

    .schedule-table tr:nth-child(odd) {
        background: #FFFFFF;
    }

    .speaker-link {
        color: rgba(0, 0, 50, 0.7);
        text-decoration: none;
        font-weight: bold;
        transition: color 0.3s ease;
    }

    .speaker-link:hover {
        color: #d1b61e;
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

<div class="schedule-section">
    <h2 class="section-title">Conference Schedule</h2>

    <!-- Tabs for filtering days -->
    <div class="tabs">
        <button 
            class="tab-button {selectedDay === 'March 10, 2025' ? 'active' : ''}" 
            on:click={() => changeDay("March 10, 2025")}>
            March 10, 2025
        </button>
        <button 
            class="tab-button {selectedDay === 'March 11, 2025' ? 'active' : ''}" 
            on:click={() => changeDay("March 11, 2025")}>
            March 11, 2025
        </button>
    </div>

    <!-- Schedule Table -->
    <table class="schedule-table">
        <thead>
            <tr>
                <th>Time</th>
                <th>Topic</th>
                <th>Speaker</th>
            </tr>
        </thead>
        <tbody>
            {#each filteredSchedule as session, index}
                <tr in:fly={{ x: -100, duration: 500, delay: index * 100 }}>
                    <td>{session.time}</td>
                    <td>{session.topic}</td>
                    <td><a href={session.link} class="speaker-link">{session.speaker}</a></td>
                </tr>
            {/each}
        </tbody>
    </table>
</div>
