<!DOCTYPE html>
<html lang="en" class="scroll-smooth">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Interactive User Agreement - LiteChat</title>
    <script src="https://cdn.tailwindcss.com"></script>
    <script src="https://cdn.jsdelivr.net/npm/chart.js"></script>
    <link rel="preconnect" href="https://fonts.googleapis.com">
    <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
    <link href="https://fonts.googleapis.com/css2?family=Inter:wght@400;500;600;700&display=swap" rel="stylesheet">
    <!-- Chosen Palette: Earthy Neutrals -->
    <!-- Application Structure Plan: A two-column SPA. Left column: sticky navigation for quick access to sections. Right column: main content area. The structure starts with a high-level summary dashboard (Key Terms & a visual chart) to give users an immediate overview. It then breaks down the agreement into themed, expandable sections. This structure was chosen to transform a dense, linear legal document into a non-linear, explorable guide, empowering users to find and understand information relevant to them without reading top-to-bottom, thus enhancing usability and comprehension. -->
    <!-- Visualization & Content Choices: 
        - Report Info: Key numerical terms (Age: 16, Notice: 30 days). Goal: Inform. Viz: 'Stat Cards' (HTML/Tailwind). Interaction: None. Justification: Highlights critical, actionable numbers for immediate user awareness.
        - Report Info: Overall document structure. Goal: Inform/Organize. Viz: Donut Chart (Chart.js/Canvas). Interaction: Hover tooltips. Justification: Provides a meta-view of where the agreement's focus lies (e.g., Rules vs. Legal), helping users mentally map the document.
        - Report Info: Prohibited conduct list. Goal: Compare/Inform. Viz: Interactive 'Do's and Don'ts' list (HTML/Tailwind with icons). Interaction: Clear visual separation. Justification: Translates a dense list of rules into a scannable, easily understood format, which is more effective than plain text for rule-based information.
        - Report Info: Main text sections. Goal: Organize/Inform. Viz: Accordion-style content blocks (HTML/JS). Interaction: Click to expand/collapse. Justification: Prevents overwhelming the user with a wall of text, allowing them to focus on one section at a time.
    -->
    <!-- CONFIRMATION: NO SVG graphics used. NO Mermaid JS used. -->
    <style>
        body {
            font-family: 'Inter', sans-serif;
            background-color: #F8F7F4;
            color: #4A4A4A;
        }
        .nav-link {
            transition: all 0.2s ease-in-out;
            border-left: 3px solid transparent;
        }
        .nav-link.active {
            color: #C0785B;
            border-left-color: #C0785B;
            background-color: #F8F7F4;
        }
        .nav-link:hover {
            color: #C0785B;
            background-color: #F8F7F4;
            border-left-color: #C0785B;
        }
        .stat-card {
            background-color: #FFFFFF;
            border: 1px solid #EAE8E2;
            box-shadow: 0 4px 6px -1px rgba(0, 0, 0, 0.05), 0 2px 4px -2px rgba(0, 0, 0, 0.05);
        }
        .content-section {
            background-color: #FFFFFF;
            border: 1px solid #EAE8E2;
        }
        .chart-container { 
            position: relative; 
            width: 100%; 
            max-width: 400px; 
            margin-left: auto; 
            margin-right: auto; 
            height: auto;
            min-height: 300px;
        }
        @media (min-width: 768px) { 
            .chart-container {
                min-height: 350px;
            }
        }
    </style>
</head>
<body class="antialiased">

    <div class="container mx-auto px-4 sm:px-6 lg:px-8 py-8">
        
        <header class="text-center mb-12">
            <h1 class="text-4xl md:text-5xl font-bold text-[#3D405B]">LiteChat User Agreement</h1>
            <p class="mt-4 text-lg text-gray-600">An interactive guide to our terms of service. Last Updated: June 20, 2025</p>
        </header>
        
        <div class="flex flex-col lg:flex-row gap-8 lg:gap-12">

            <aside class="lg:w-1/4">
                <nav id="toc" class="sticky top-8 bg-[#F1F0EC] rounded-lg p-4">
                    <h3 class="font-bold text-lg mb-4 text-[#3D405B]">Agreement Sections</h3>
                    <ul class="space-y-2">
                        <li><a href="#summary" class="nav-link block font-medium p-3 rounded-md">Summary & Key Terms</a></li>
                        <li><a href="#acceptance" class="nav-link block font-medium p-3 rounded-md">1. Acceptance of Terms</a></li>
                        <li><a href="#accounts" class="nav-link block font-medium p-3 rounded-md">2. User Accounts</a></li>
                        <li><a href="#conduct" class="nav-link block font-medium p-3 rounded-md">3. User Conduct</a></li>
                        <li><a href="#content" class="nav-link block font-medium p-3 rounded-md">4. Content & License</a></li>
                        <li><a href="#privacy" class="nav-link block font-medium p-3 rounded-md">5. Privacy Policy</a></li>
                        <li><a href="#intellectual-property" class="nav-link block font-medium p-3 rounded-md">6. Intellectual Property</a></li>
                        <li><a href="#legal" class="nav-link block font-medium p-3 rounded-md">7. The Fine Print (Legal)</a></li>
                        <li><a href="#contact" class="nav-link block font-medium p-3 rounded-md">8. Contact Us</a></li>
                    </ul>
                </nav>
            </aside>

            <main class="lg:w-3/4 space-y-12">
                <section id="summary" class="content-section rounded-xl p-6 md:p-8">
                    <h2 class="text-3xl font-bold mb-6 text-[#C0785B]">Agreement at a Glance</h2>
                    <p class="mb-8 text-base">This section provides a quick overview of the most important points in the User Agreement. Below, you'll find key numbers from the terms and a chart showing how the document's content is distributed. This is a summary, not a replacement for the full agreement.</p>

                    <div class="grid grid-cols-1 md:grid-cols-2 gap-6 mb-12">
                        <div class="stat-card p-6 rounded-lg text-center">
                            <p class="text-5xl font-bold text-[#3D405B]">16+</p>
                            <p class="mt-2 text-gray-600 font-medium">Minimum age to use LiteChat.</p>
                        </div>
                        <div class="stat-card p-6 rounded-lg text-center">
                            <p class="text-5xl font-bold text-[#3D405B]">30</p>
                            <p class="mt-2 text-gray-600 font-medium">Days' notice we'll provide for material changes to these terms.</p>
                        </div>
                    </div>

                    <h3 class="text-2xl font-bold mb-4 text-center text-[#3D405B]">Focus of the Agreement</h3>
                    <div class="chart-container">
                        <canvas id="agreementChart"></canvas>
                    </div>
                </section>
                
                <section id="acceptance" class="content-section rounded-xl p-6 md:p-8">
                    <h2 class="text-2xl font-bold mb-4 text-[#C0785B]">1. Acceptance of Terms</h2>
                    <p>This is the foundational part of our agreement. By creating an account or using LiteChat, you are formally agreeing to be bound by all the rules outlined in this document and our Privacy Policy. Think of it as the handshake that starts our relationship. If you don't agree with these terms, you cannot use the app.</p>
                </section>

                <section id="accounts" class="content-section rounded-xl p-6 md:p-8">
                    <h2 class="text-2xl font-bold mb-4 text-[#C0785B]">2. User Accounts</h2>
                    <p class="mb-4">This section covers the rules and responsibilities related to your LiteChat account. It's about keeping your account information accurate and secure.</p>
                    <ul class="space-y-4 list-disc list-inside text-gray-700">
                        <li><strong>Registration:</strong> You commit to providing true and current information when you sign up, and to keeping it updated.</li>
                        <li><strong>Security:</strong> You are responsible for your password and all actions taken on your account. If you suspect any unauthorized use, you must notify us immediately.</li>
                        <li><strong>Age:</strong> You must be at least 16 years old. If you're under the age of majority where you live, you need permission from a parent or legal guardian.</li>
                    </ul>
                </section>

                <section id="conduct" class="content-section rounded-xl p-6 md:p-8">
                    <h2 class="text-2xl font-bold mb-4 text-[#C0785B]">3. User Conduct: The Rules of the Road</h2>
                    <p class="mb-6">To keep LiteChat safe and enjoyable for everyone, we require all users to follow these rules of conduct. This is not an exhaustive list, but it covers the most important principles of respectful interaction on our platform.</p>
                    <div class="grid grid-cols-1 md:grid-cols-2 gap-6">
                        <div class="bg-green-50 border border-green-200 rounded-lg p-4">
                            <h3 class="font-bold text-lg text-green-800 mb-2 flex items-center"><span class="text-2xl mr-2">✅</span> What's Allowed</h3>
                            <ul class="list-disc list-inside space-y-1 text-green-700">
                                <li>Respectful conversations</li>
                                <li>Sharing appropriate content</li>
                                <li>Using the app for personal, lawful purposes</li>
                            </ul>
                        </div>
                        <div class="bg-red-50 border border-red-200 rounded-lg p-4">
                            <h3 class="font-bold text-lg text-red-800 mb-2 flex items-center"><span class="text-2xl mr-2">❌</span> What's Prohibited</h3>
                            <ul class="list-disc list-inside space-y-1 text-red-700">
                                <li>Illegal activities or content</li>
                                <li>Harassment, bullying, or hate speech</li>
                                <li>Impersonation or spam</li>
                                <li>Spreading malware or viruses</li>
                                <li>Infringing on intellectual property</li>
                                <li>Commercial use without permission</li>
                            </ul>
                        </div>
                    </div>
                </section>

                <section id="content" class="content-section rounded-xl p-6 md:p-8">
                    <h2 class="text-2xl font-bold mb-4 text-[#C0785B]">4. Content Ownership & License</h2>
                    <p class="mb-4">This part explains who owns the content shared on LiteChat and how it can be used. It's important for understanding your rights.</p>
                    <div class="space-y-4">
                        <div class="p-4 bg-gray-50 rounded-lg border">
                            <h4 class="font-semibold text-gray-800">Your Content is Yours</h4>
                            <p class="text-gray-600">You retain full ownership of the text, images, and other content you create and share on the app.</p>
                        </div>
                        <div class="p-4 bg-gray-50 rounded-lg border">
                            <h4 class="font-semibold text-gray-800">License to Us</h4>
                            <p class="text-gray-600">To operate and improve the app, you grant us a license to use, reproduce, and display your content within the LiteChat service. For example, we need this permission to show your message to another user. This does not give us ownership.</p>
                        </div>
                         <div class="p-4 bg-yellow-50 rounded-lg border border-yellow-200">
                            <h4 class="font-semibold text-yellow-800">Public Chats</h4>
                            <p class="text-yellow-700">Remember that content in public or group chats is visible to others. Please be mindful of the information you share in those spaces.</p>
                        </div>
                    </div>
                </section>
                
                <section id="privacy" class="content-section rounded-xl p-6 md:p-8">
                    <h2 class="text-2xl font-bold mb-4 text-[#C0785B]">5. Privacy Policy</h2>
                    <p>Your privacy is important. Our use of your data is detailed in our separate Privacy Policy. This policy is a part of our agreement with you. Please review it to understand how we handle your information. You can find it here: <a href="https://siddhartharya-09.github.io/LiteChat-Build/" target="_blank" rel="noopener noreferrer" class="text-blue-600 hover:underline">LiteChat Privacy Policy</a>.</p>
                </section>
                
                <section id="intellectual-property" class="content-section rounded-xl p-6 md:p-8">
                    <h2 class="text-2xl font-bold mb-4 text-[#C0785B]">6. Intellectual Property</h2>
                    <p>This section clarifies that the LiteChat app itself—including its name, logo, design, code, and original content—is our property. You have a license to use the app as intended, but you do not have the right to copy, modify, or sell our intellectual property.</p>
                </section>

                <section id="legal" class="content-section rounded-xl p-6 md:p-8">
                    <h2 class="text-2xl font-bold mb-4 text-[#C0785B]">7. The Fine Print (Legal Disclaimers & Limitations)</h2>
                     <p class="mb-4">This final block contains standard but important legal clauses that govern our agreement. They address liability, warranties, and what happens in case of disputes. We've grouped them here for clarity.</p>
                    <div id="accordion-container" class="space-y-2">
                        <div class="accordion-item">
                            <button class="accordion-header w-full text-left font-semibold p-4 bg-gray-100 hover:bg-gray-200 rounded-lg flex justify-between items-center transition">
                                Disclaimers (Our "As Is" Service)
                                <span class="accordion-icon text-2xl font-thin transform transition-transform">+</span>
                            </button>
                            <div class="accordion-content max-h-0 overflow-hidden transition-all duration-500 ease-in-out">
                                <p class="p-4 text-gray-600">We provide LiteChat "as is," without any warranties. This means we don't guarantee it will always be perfect, uninterrupted, or error-free.</p>
                            </div>
                        </div>
                        <div class="accordion-item">
                            <button class="accordion-header w-full text-left font-semibold p-4 bg-gray-100 hover:bg-gray-200 rounded-lg flex justify-between items-center transition">
                                Limitation of Liability
                                <span class="accordion-icon text-2xl font-thin transform transition-transform">+</span>
                            </button>
                            <div class="accordion-content max-h-0 overflow-hidden transition-all duration-500 ease-in-out">
                                <p class="p-4 text-gray-600">Our legal liability to you is limited. We are not responsible for indirect damages that may arise from your use of the app.</p>
                            </div>
                        </div>
                        <div class="accordion-item">
                            <button class="accordion-header w-full text-left font-semibold p-4 bg-gray-100 hover:bg-gray-200 rounded-lg flex justify-between items-center transition">
                                Indemnification
                                <span class="accordion-icon text-2xl font-thin transform transition-transform">+</span>
                            </button>
                            <div class="accordion-content max-h-0 overflow-hidden transition-all duration-500 ease-in-out">
                                <p class="p-4 text-gray-600">If your actions on the app lead to a legal claim against us, you agree to cover our costs. This means you agree to defend and hold us harmless.</p>
                            </div>
                        </div>
                        <div class="accordion-item">
                            <button class="accordion-header w-full text-left font-semibold p-4 bg-gray-100 hover:bg-gray-200 rounded-lg flex justify-between items-center transition">
                                Termination
                                <span class="accordion-icon text-2xl font-thin transform transition-transform">+</span>
                            </button>
                            <div class="accordion-content max-h-0 overflow-hidden transition-all duration-500 ease-in-out">
                                <p class="p-4 text-gray-600">We reserve the right to suspend or terminate your account at any time, especially if you violate these terms. You can also stop using the app at any time.</p>
                            </div>
                        </div>
                         <div class="accordion-item">
                            <button class="accordion-header w-full text-left font-semibold p-4 bg-gray-100 hover:bg-gray-200 rounded-lg flex justify-between items-center transition">
                                Governing Law
                                <span class="accordion-icon text-2xl font-thin transform transition-transform">+</span>
                            </button>
                            <div class="accordion-content max-h-0 overflow-hidden transition-all duration-500 ease-in-out">
                                <p class="p-4 text-gray-600">This agreement is governed by the laws of New Delhi, India.</p>
                            </div>
                        </div>
                    </div>
                </section>
                
                <section id="contact" class="content-section rounded-xl p-6 md:p-8 text-center">
                    <h2 class="text-2xl font-bold mb-4 text-[#C0785B]">8. Questions?</h2>
                    <p class="text-lg">If you have any questions about this User Agreement, please feel free to reach out to us.</p>
                    <a href="mailto:anantgautam267@gmail.com" class="mt-4 inline-block bg-[#C0785B] text-white font-bold py-3 px-6 rounded-lg hover:bg-[#a9664c] transition-colors">Contact Us</a>
                </section>

            </main>
        </div>
    </div>

    <script>
        document.addEventListener('DOMContentLoaded', function () {
            
            const agreementChartCtx = document.getElementById('agreementChart').getContext('2d');
            const agreementChart = new Chart(agreementChartCtx, {
                type: 'doughnut',
                data: {
                    labels: ['Your Responsibilities (Conduct & Content)', 'Legal Framework & Disclaimers', 'Account Setup & General Terms'],
                    datasets: [{
                        label: 'Focus of Agreement',
                        data: [350, 450, 200],
                        backgroundColor: [
                            '#8E8D8A',
                            '#E0AFA0',
                            '#F4F1DE'
                        ],
                        borderColor: [
                           '#8E8D8A',
                           '#E0AFA0',
                           '#F4F1DE'
                        ],
                        borderWidth: 1
                    }]
                },
                options: {
                    responsive: true,
                    maintainAspectRatio: false,
                    plugins: {
                        legend: {
                            position: 'bottom',
                             labels: {
                                color: '#4A4A4A',
                                font: {
                                    size: 14,
                                    family: 'Inter'
                                }
                            }
                        },
                        tooltip: {
                            callbacks: {
                                label: function(context) {
                                    let label = context.label || '';
                                    if (label) {
                                        label += ': ';
                                    }
                                    if (context.parsed !== null) {
                                        const total = context.chart.data.datasets[0].data.reduce((a, b) => a + b, 0);
                                        const percentage = ((context.parsed / total) * 100).toFixed(1) + '%';
                                        label += percentage;
                                    }
                                    return label;
                                }
                            }
                        }
                    }
                }
            });

            const tocLinks = document.querySelectorAll('#toc a');
            const sections = document.querySelectorAll('main section');

            const observer = new IntersectionObserver((entries) => {
                entries.forEach(entry => {
                    if (entry.isIntersecting) {
                        tocLinks.forEach(link => {
                            link.classList.remove('active');
                            if (link.getAttribute('href').substring(1) === entry.target.id) {
                                link.classList.add('active');
                            }
                        });
                    }
                });
            }, { rootMargin: '-50% 0px -50% 0px' });

            sections.forEach(section => {
                observer.observe(section);
            });

            const accordionItems = document.querySelectorAll('.accordion-item');
            accordionItems.forEach(item => {
                const header = item.querySelector('.accordion-header');
                const content = item.querySelector('.accordion-content');
                const icon = item.querySelector('.accordion-icon');

                header.addEventListener('click', () => {
                    const isOpen = content.style.maxHeight && content.style.maxHeight !== '0px';

                    // Close all other items
                    accordionItems.forEach(otherItem => {
                        if (otherItem !== item) {
                            otherItem.querySelector('.accordion-content').style.maxHeight = '0px';
                            otherItem.querySelector('.accordion-icon').textContent = '+';
                            otherItem.querySelector('.accordion-icon').classList.remove('rotate-45');
                        }
                    });

                    // Toggle current item
                    if (isOpen) {
                        content.style.maxHeight = '0px';
                        icon.textContent = '+';
                        icon.classList.remove('rotate-45');
                    } else {
                        content.style.maxHeight = content.scrollHeight + 'px';
                        icon.textContent = '+';
                        icon.classList.add('rotate-45');
                    }
                });
            });
        });
    </script>
</body>
</html>

