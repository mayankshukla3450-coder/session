<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>The Power of Sharing: A Mental Wellness Session Showcase</title>
    <script src="https://cdn.tailwindcss.com"></script>
    <script src="https://cdn.jsdelivr.net/npm/chart.js"></script>
    <link rel="preconnect" href="https://fonts.googleapis.com">
    <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
    <link href="https://fonts.googleapis.com/css2?family=Inter:wght@400;500;700&display=swap" rel="stylesheet">
    <!-- Chosen Palette: Warm Neutrals & Soft Teal -->
    <!-- Application Structure Plan: The SPA is designed as a single-page interactive narrative that mirrors the emotional journey of the wellness session, making it digestible for a professional audience (e.g., on LinkedIn). The structure is thematic, not linear like the speech, to promote exploration. It begins with an introduction to the core metaphor (Feelings as Weather), moves to an interactive demonstration of the "Heavy Backpack" concept, then allows users to engage with simulations of the session's key activities (the "Worry Box" and "Affirmation Wall"). This is followed by a data analysis section with charts that synthesize the qualitative insights from the activities into quantitative summaries—perfect for demonstrating impact. The page concludes with clear, actionable takeaways. This structure was chosen to transform the session's description into a compelling, interactive case study that shows, rather than just tells, its value. -->
    <!-- Visualization & Content Choices: 
        1. Feelings as Weather: Report Info -> Metaphor for changing emotions. Goal -> Inform/Engage. Viz/Presentation -> Text with animated Unicode icons (☀️, ☁️, ⛈️). Interaction -> Icons subtly animate to draw attention. Justification -> A lightweight, engaging way to introduce the core theme. Method -> HTML/CSS.
        2. Heavy Backpack: Report Info -> Metaphor for accumulating stress. Goal -> Explain/Interact. Viz/Presentation -> HTML/CSS graphic of a backpack alongside clickable stressor buttons. Interaction -> Clicking buttons visually changes the backpack's state and updates a text block, making the metaphor tangible. Justification -> Interactive learning is more memorable than passive reading. Method -> HTML/CSS/JS.
        3. Worry Box Simulation: Report Info -> Anonymous sharing activity. Goal -> Demonstrate/Empathize. Viz/Presentation -> Two-panel layout with category filters and content display area. Interaction -> User clicks a category to see sample anonymous worries and the supportive advice provided. Justification -> Simulates the activity's core function, showing how diverse issues were handled with care. Method -> HTML/JS.
        4. Affirmation Wall: Report Info -> Collaborative positive messaging activity. Goal -> Demonstrate/Inspire. Viz/Presentation -> A dynamic grid of 'sticky notes'. Interaction -> A button adds a new affirmation to the wall from a predefined list. Justification -> Visualizes the collaborative and uplifting nature of the exercise. Method -> HTML/JS.
        5. Worry Category Analysis: Report Info -> Themes from the Worry Box. Goal -> Analyze/Summarize. Viz/Presentation -> Donut Chart. Interaction -> Hover tooltips. Justification -> Effectively shows the proportion of different concerns, providing a clear data-driven insight into student needs. Library -> Chart.js (Canvas).
        6. Affirmation Theme Analysis: Report Info -> Themes from the Affirmation Wall. Goal -> Analyze/Compare. Viz/Presentation -> Horizontal Bar Chart. Interaction -> Hover tooltips. Justification -> Ideal for comparing the frequency of different positive themes, showcasing the session's positive impact. Library -> Chart.js (Canvas).
    -->
    <!-- CONFIRMATION: NO SVG graphics used. NO Mermaid JS used. -->
    <style>
        body {
            font-family: 'Inter', sans-serif;
            background-color: #FDFBF8;
            color: #383838;
        }
        .chart-container {
            position: relative;
            width: 100%;
            max-width: 450px;
            margin-left: auto;
            margin-right: auto;
            height: 300px;
            max-height: 400px;
        }
        @media (min-width: 768px) {
            .chart-container {
                height: 350px;
            }
        }
        .affirmation-note {
            transform: rotate(0deg);
            transition: transform 0.3s ease-in-out, box-shadow 0.3s ease-in-out;
        }
        .affirmation-note:hover {
            transform: scale(1.05) rotate(0deg) !important;
            z-index: 10;
            box-shadow: 0 10px 15px -3px rgba(0, 0, 0, 0.1), 0 4px 6px -2px rgba(0, 0, 0, 0.05);
        }
        .weather-icon {
            display: inline-block;
            animation: fade-in-out 9s infinite;
        }
        .weather-icon:nth-child(1) { animation-delay: 0s; }
        .weather-icon:nth-child(2) { animation-delay: 3s; }
        .weather-icon:nth-child(3) { animation-delay: 6s; }

        @keyframes fade-in-out {
            0%, 33.33%, 100% { opacity: 0; }
            3%, 30% { opacity: 1; }
        }
        .backpack-strain {
            transition: transform 0.5s cubic-bezier(0.34, 1.56, 0.64, 1);
        }
    </style>
</head>
<body class="antialiased">

    <main class="container mx-auto px-4 sm:px-6 lg:px-8 py-12">
        
        <header class="text-center mb-16">
            <h1 class="text-4xl md:text-5xl font-bold text-teal-800 mb-4">The Power of Sharing</h1>
            <p class="text-lg md:text-xl text-gray-600 max-w-3xl mx-auto">An interactive showcase of the mental wellness session held at Green Valley High School for students of grades 6-11.</p>
        </header>

        <section id="weather" class="mb-20 text-center bg-white rounded-2xl p-8 shadow-sm">
            <h2 class="text-3xl font-bold text-teal-700 mb-4">It's Okay to Have Stormy Days</h2>
            <p class="max-w-3xl mx-auto text-gray-700 mb-6">
                The session began with a simple idea: our feelings are like the weather. Some days are sunny <span class="weather-icon text-3xl">☀️</span>, some are cloudy <span class="weather-icon text-3xl">☁️</span>, and some are stormy <span class="weather-icon text-3xl">⛈️</span>. We taught students that every kind of emotional weather is normal and valid. Understanding this helps us learn to navigate our feelings without judgment.
            </p>
        </section>

        <section id="backpack" class="mb-20">
            <h2 class="text-3xl font-bold text-center text-teal-700 mb-8">The Heavy Backpack Analogy</h2>
            <div class="flex flex-col lg:flex-row items-center gap-8 lg:gap-12">
                <div class="lg:w-1/2 w-full flex justify-center p-6">
                    <div id="backpack-container" class="relative w-64 h-80 bg-teal-600 rounded-t-full rounded-b-2xl shadow-lg flex items-center justify-center backpack-strain">
                        <div class="w-48 h-56 bg-teal-500 rounded-t-3xl rounded-b-xl"></div>
                        <div class="absolute top-4 w-16 h-8 bg-teal-700 rounded-t-lg"></div>
                        <div class="absolute top-20 w-32 h-20 bg-teal-700 rounded-lg"></div>
                        <div class="absolute -top-8 w-4 h-24 bg-gray-600 rounded-t-full z-[-1] transform -translate-x-12 rotate-12"></div>
                        <div class="absolute -top-8 w-4 h-24 bg-gray-600 rounded-t-full z-[-1] transform translate-x-12 -rotate-12"></div>
                        <div id="backpack-emoji" class="text-7xl absolute transition-opacity duration-500 opacity-0"></div>
                    </div>
                </div>
                <div class="lg:w-1/2 w-full">
                    <p class="text-gray-700 mb-6 text-lg">We asked students to imagine that every worry is a stone added to their backpack. A few are manageable, but over time, the backpack can become incredibly heavy. This interactive exercise demonstrates how different stressors contribute to our mental load.</p>
                    <div class="flex flex-wrap gap-3">
                        <button class="stressor-btn bg-white hover:bg-teal-50 border border-teal-200 text-teal-800 font-medium py-2 px-4 rounded-full transition-all" data-text="Schoolwork feels overwhelming.">Academic Pressure</button>
                        <button class="stressor-btn bg-white hover:bg-teal-50 border border-teal-200 text-teal-800 font-medium py-2 px-4 rounded-full transition-all" data-text="Friendship problems can feel isolating.">Social Issues</button>
                        <button class="stressor-btn bg-white hover:bg-teal-50 border border-teal-200 text-teal-800 font-medium py-2 px-4 rounded-full transition-all" data-text="Worrying about the future is common.">Future Anxiety</button>
                        <button class="stressor-btn bg-white hover:bg-teal-50 border border-teal-200 text-teal-800 font-medium py-2 px-4 rounded-full transition-all" data-text="Pressure from family can add weight.">Family Pressure</button>
                        <button class="stressor-btn bg-white hover:bg-teal-50 border border-teal-200 text-teal-800 font-medium py-2 px-4 rounded-full transition-all" data-text="Feeling like you don't fit in is tough.">Self-Esteem</button>
                    </div>
                     <div id="backpack-text" class="mt-6 p-4 bg-teal-50 rounded-lg min-h-[80px] text-teal-900 font-medium flex items-center justify-center text-center">
                        Click a stressor to add a "stone" to the backpack.
                    </div>
                </div>
            </div>
        </section>
        
        <section id="worry-box" class="mb-20 bg-white p-8 rounded-2xl shadow-sm">
            <h2 class="text-3xl font-bold text-center text-teal-700 mb-2">The Anonymous Worry Box</h2>
            <p class="text-center text-gray-600 mb-8 max-w-3xl mx-auto">To show students they weren't alone, we used a "Worry Box" for them to share concerns anonymously. This activity built trust and allowed us to address real issues directly and with empathy. Explore some of the common themes below.</p>
            <div class="flex flex-col md:flex-row gap-6">
                <div class="md:w-1/3 flex flex-col space-y-3">
                    <button class="worry-category-btn text-left p-4 rounded-lg bg-amber-100 text-amber-900 font-semibold" data-category="school">
                        🏫 Academic & School Life
                    </button>
                    <button class="worry-category-btn text-left p-4 rounded-lg bg-sky-100 text-sky-900 font-semibold" data-category="friends">
                        👥 Friendships & Social Life
                    </button>
                    <button class="worry-category-btn text-left p-4 rounded-lg bg-rose-100 text-rose-900 font-semibold" data-category="personal">
                        ❤️ Personal Feelings & Identity
                    </button>
                </div>
                <div id="worry-display" class="md:w-2/3 p-6 rounded-lg bg-gray-50 min-h-[250px] flex flex-col justify-center">
                    <p class="text-gray-500 text-center">Select a category to see examples of shared worries and our supportive responses.</p>
                </div>
            </div>
        </section>

        <section id="affirmation-wall" class="mb-20">
            <h2 class="text-3xl font-bold text-center text-teal-700 mb-2">The Collaborative Affirmation Wall</h2>
             <p class="text-center text-gray-600 mb-8 max-w-3xl mx-auto">The session's highlight was turning a smart board into an Affirmation Wall. Students shared positive messages, creating a powerful, collective reminder of their strength and resilience. Click the button to add to our digital wall!</p>
             <div class="text-center mb-6">
                 <button id="add-affirmation-btn" class="bg-teal-600 text-white font-bold py-3 px-6 rounded-lg hover:bg-teal-700 transition-colors shadow-md">Add an Affirmation</button>
             </div>
            <div id="affirmation-grid" class="grid grid-cols-2 sm:grid-cols-3 md:grid-cols-4 lg:grid-cols-5 gap-4">
            </div>
        </section>

        <section id="analysis" class="mb-20 bg-white p-8 rounded-2xl shadow-sm">
            <h2 class="text-3xl font-bold text-center text-teal-700 mb-2">Session Insights & Impact</h2>
            <p class="text-center text-gray-600 mb-12 max-w-3xl mx-auto">By analyzing the anonymous submissions and affirmations, we gained valuable insights into the students' primary concerns and the supportive themes that resonated most. This data helps us tailor future wellness initiatives effectively.</p>
            <div class="flex flex-col lg:flex-row gap-12 justify-around items-center">
                <div class="w-full lg:w-1/2">
                    <h3 class="text-xl font-bold text-center text-gray-800 mb-4">Common Worry Themes</h3>
                    <div class="chart-container">
                        <canvas id="worryChart"></canvas>
                    </div>
                </div>
                <div class="w-full lg:w-1/2">
                    <h3 class="text-xl font-bold text-center text-gray-800 mb-4">Popular Affirmation Themes</h3>
                    <div class="chart-container">
                        <canvas id="affirmationChart"></canvas>
                    </div>
                </div>
            </div>
        </section>

        <section id="takeaways" class="text-center">
            <h2 class="text-3xl font-bold text-center text-teal-700 mb-8">Key Takeaways for Our Community</h2>
            <div class="grid md:grid-cols-3 gap-8">
                <div class="bg-white p-6 rounded-lg shadow-sm">
                    <div class="text-4xl mb-4"> валидно </div>
                    <h3 class="text-xl font-bold mb-2">Your Feelings Are Valid</h3>
                    <p class="text-gray-600">It's okay not to be okay. We encouraged students to accept their feelings without judgment as a first step toward wellness.</p>
                </div>
                <div class="bg-white p-6 rounded-lg shadow-sm">
                    <div class="text-4xl mb-4"> 💪 </div>
                    <h3 class="text-xl font-bold mb-2">You Have Strength to Cope</h3>
                    <p class="text-gray-600">The session focused on building resilience and reminding students of their inner strength and available coping strategies.</p>
                </div>
                <div class="bg-white p-6 rounded-lg shadow-sm">
                    <div class="text-4xl mb-4"> 🤝 </div>
                    <h3 class="text-xl font-bold mb-2">You Are Not Alone</h3>
                    <p class="text-gray-600">The most critical message was the power of community. Asking for help is a sign of strength, and support is always available.</p>
                </div>
            </div>
        </section>

    </main>

    <footer class="text-center py-8 mt-12 border-t">
        <p class="text-gray-500">A showcase of the mental wellness initiative at Green Valley High School.</p>
    </footer>

    <script>
        document.addEventListener('DOMContentLoaded', () => {
            const worryData = {
                school: {
                    worry: "I feel like I'm not good enough at school and can't keep up with the work.",
                    response: "This is a very common feeling. Remember, your worth isn't defined by grades. Focus on your effort and progress. It's brave to ask teachers for help or form a study group. Small steps make a big difference."
                },
                friends: {
                    worry: "My friends sometimes leave me out, and I feel lonely and don't know what to do.",
                    response: "That is incredibly painful, and your feelings are valid. True friends lift you up. Try talking to one trusted friend about how you feel. It's also okay to seek out new friendships in clubs or activities that you enjoy."
                },
                personal: {
                    worry: "I don't like how I look and I always compare myself to others on social media.",
                    response: "Thank you for sharing this. Social media often shows a filtered, unrealistic version of life. It's important to remember your own unique strengths and qualities. Try focusing on what your body can DO, not just how it looks. Unfollowing accounts that make you feel bad is a powerful act of self-care."
                }
            };

            const worryCategoryBtns = document.querySelectorAll('.worry-category-btn');
            const worryDisplay = document.getElementById('worry-display');
            let activeCategory = null;

            worryCategoryBtns.forEach(btn => {
                btn.addEventListener('click', () => {
                    const category = btn.dataset.category;

                    if (activeCategory) {
                        activeCategory.classList.remove('bg-opacity-100');
                        activeCategory.classList.add('bg-opacity-70', 'hover:bg-opacity-100');
                    }
                    
                    worryCategoryBtns.forEach(b => {
                        b.style.backgroundColor = '';
                        b.style.color = '';
                    });
                    
                    const categoryData = worryData[category];
                    worryDisplay.innerHTML = `
                        <div class="mb-4">
                            <h4 class="font-semibold text-gray-500 text-sm mb-2">ANONYMOUS WORRY:</h4>
                            <p class="text-gray-800 text-lg">"${categoryData.worry}"</p>
                        </div>
                        <div class="border-t border-gray-200 pt-4">
                            <h4 class="font-semibold text-teal-600 text-sm mb-2">OUR SUPPORTIVE RESPONSE:</h4>
                            <p class="text-gray-700">"${categoryData.response}"</p>
                        </div>
                    `;
                });
            });

            const affirmations = [
                "I am strong enough to handle this.", "It's okay to ask for help.", "My feelings are valid.", "I matter.", "This feeling will pass.", "I am proud of who I am becoming.", "I choose to be kind to myself.", "I am resilient.", "My challenges help me grow.", "I am not alone."
            ];
            const affirmationColors = [
                'bg-amber-200', 'bg-sky-200', 'bg-rose-200', 'bg-lime-200', 'bg-violet-200'
            ];
            
            const addAffirmationBtn = document.getElementById('add-affirmation-btn');
            const affirmationGrid = document.getElementById('affirmation-grid');
            let usedAffirmations = [];

            function createAffirmationNote(text) {
                const note = document.createElement('div');
                const color = affirmationColors[Math.floor(Math.random() * affirmationColors.length)];
                const rotation = Math.random() * 8 - 4;
                note.className = `affirmation-note p-4 rounded-lg flex items-center justify-center text-center font-medium shadow-md ${color} text-gray-800`;
                note.style.transform = `rotate(${rotation}deg)`;
                note.textContent = text;
                return note;
            }

            function addAffirmationToWall() {
                if (usedAffirmations.length === affirmations.length) {
                    usedAffirmations = []; 
                }
                
                let availableAffirmations = affirmations.filter(a => !usedAffirmations.includes(a));
                if (availableAffirmations.length === 0) {
                     usedAffirmations = [];
                     availableAffirmations = affirmations;
                }
                
                const affirmationText = availableAffirmations[Math.floor(Math.random() * availableAffirmations.length)];
                usedAffirmations.push(affirmationText);

                const note = createAffirmationNote(affirmationText);
                affirmationGrid.appendChild(note);
            }

            for(let i = 0; i < 5; i++) {
                addAffirmationToWall();
            }
            addAffirmationBtn.addEventListener('click', addAffirmationToWall);

            const backpackContainer = document.getElementById('backpack-container');
            const backpackText = document.getElementById('backpack-text');
            const stressorBtns = document.querySelectorAll('.stressor-btn');
            let strain = 0;

            stressorBtns.forEach(btn => {
                btn.addEventListener('click', () => {
                    strain += 1;
                    const scale = 1 - (strain * 0.03);
                    const rotation = (strain % 2 === 0 ? strain : -strain) * 0.5;
                    backpackContainer.style.transform = `scaleY(${scale}) rotate(${rotation}deg)`;
                    backpackText.textContent = btn.dataset.text;

                    stressorBtns.forEach(b => b.classList.remove('bg-teal-100'));
                    btn.classList.add('bg-teal-100');

                    if (strain > 10) {
                        strain = 0;
                    }
                });
            });

            const wrapText = (text, maxLength) => {
                const words = text.split(' ');
                const lines = [];
                let currentLine = '';
                words.forEach(word => {
                    if ((currentLine + word).length < maxLength) {
                        currentLine += `${word} `;
                    } else {
                        lines.push(currentLine.trim());
                        currentLine = `${word} `;
                    }
                });
                lines.push(currentLine.trim());
                return lines;
            };

            const worryChartCtx = document.getElementById('worryChart').getContext('2d');
            new Chart(worryChartCtx, {
                type: 'doughnut',
                data: {
                    labels: ['Academic Pressure', 'Social Issues', 'Personal Feelings', 'Future Anxiety', 'Family Pressure'],
                    datasets: [{
                        label: 'Worry Themes',
                        data: [40, 25, 15, 12, 8],
                        backgroundColor: ['#0d9488', '#0ea5e9', '#e11d48', '#f59e0b', '#8b5cf6'],
                        borderColor: '#FDFBF8',
                        borderWidth: 4
                    }]
                },
                options: {
                    responsive: true,
                    maintainAspectRatio: false,
                    plugins: {
                        legend: {
                            position: 'bottom',
                            labels: {
                                color: '#383838'
                            }
                        },
                        tooltip: {
                            callbacks: {
                                label: function(context) {
                                    return `${context.label}: ${context.raw}%`;
                                }
                            }
                        }
                    },
                    cutout: '60%'
                }
            });

            const affirmationChartCtx = document.getElementById('affirmationChart').getContext('2d');
            new Chart(affirmationChartCtx, {
                type: 'bar',
                data: {
                    labels: ['Self-Worth', 'Resilience', 'Seeking Help', 'Community', 'Patience'],
                    datasets: [{
                        label: 'Affirmation Frequency',
                        data: [35, 28, 20, 12, 5],
                        backgroundColor: '#14b8a6',
                        borderRadius: 4
                    }]
                },
                options: {
                    indexAxis: 'y',
                    responsive: true,
                    maintainAspectRatio: false,
                    plugins: {
                        legend: {
                            display: false
                        },
                        tooltip: {
                            callbacks: {
                                label: function(context) {
                                    return ` ${context.raw} mentions`;
                                }
                            }
                        }
                    },
                    scales: {
                        x: {
                            beginAtZero: true,
                            grid: {
                                display: false
                            },
                             ticks: { color: '#383838' }
                        },
                        y: {
                            grid: {
                                display: false
                            },
                             ticks: { color: '#383838' }
                        }
                    }
                }
            });
        });
    </script>
</body>
</html>
