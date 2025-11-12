# Review-cards-Monte
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>CSS Flashcard Review</title>
    <!-- Load Tailwind CSS -->
    <script src="https://cdn.tailwindcss.com"></script>
    <style>
        /* Load Inter font for aesthetics */
        @import url('https://fonts.googleapis.com/css2?family=Inter:wght@100..900&display=swap');
        
        :root {
            /* Define colors for easy customization */
            --card-color: #1f2937; /* Dark Slate Gray */
            --accent-color: #8b5cf6; /* Violet 500 */
        }

        body {
            font-family: 'Inter', sans-serif;
            background-color: #f3f4f6; /* Light Gray Background */
        }

        /* 1. Initial Animation Keyframes: The title will dramatically drop, slightly zoom, and pulse */
        @keyframes header-drop {
            0% {
                opacity: 0;
                transform: translateY(-50px) scale(0.8);
                text-shadow: 0 0 10px rgba(139, 92, 246, 0);
            }
            70% {
                opacity: 1;
                transform: translateY(0) scale(1.05);
                text-shadow: 0 0 10px rgba(139, 92, 246, 0.5); /* Slight shadow pulse */
            }
            100% {
                opacity: 1;
                transform: translateY(0) scale(1);
                text-shadow: 0 0 10px rgba(139, 92, 246, 0);
            }
        }

        /* Apply initial animation on page load */
        #page-title {
            animation: header-drop 1.5s ease-out 1 forwards;
        }

        /* 2. Card Styling and Reveal Transition Setup */
        .flashcard {
            background-color: var(--card-color);
            color: white;
            /* Default shadow and transition for hover effects */
            box-shadow: 0 10px 15px -3px rgba(0, 0, 0, 0.1), 0 4px 6px -2px rgba(0, 0, 0, 0.05);
            transition: all 0.3s ease-in-out;
            border: 3px solid transparent; /* Border for hover feedback */
        }

        /* Hover effect: lift and add accent border */
        .flashcard:hover {
            transform: translateY(-5px) scale(1.02);
            box-shadow: 0 20px 25px -5px rgba(0, 0, 0, 0.2), 0 8px 10px -6px rgba(0, 0, 0, 0.1);
            border-color: var(--accent-color);
        }

        /* Answer content initial state (HIDDEN) */
        .answer-content {
            /* These properties are transitioned to create the creative reveal effect */
            opacity: 0;
            max-height: 0;
            overflow: hidden;
            transform: scale(0.95) translateY(-10px); /* Start slightly smaller and higher */
            
            /* Custom transition for a smooth, sequential effect */
            transition: opacity 0.4s ease-out, max-height 0.6s ease-out, transform 0.4s ease-out;
            padding-top: 0; /* Ensures max-height works correctly */
        }
        
        /* Card hover state (REVEALED) */
        .flashcard:hover .answer-content {
            opacity: 1;
            max-height: 200px; /* Expands to reveal content */
            transform: scale(1) translateY(0); /* Zooms up and moves down into place */
            padding-top: 1.5rem; /* Reintroduces visual spacing */
        }

        .question-text {
            border-bottom: 2px solid rgba(255, 255, 255, 0.1);
            padding-bottom: 1.5rem;
        }
    </style>
</head>
<body class="p-4 md:p-8">

    <!-- Title Section with On-Load Animation -->
    <header class="text-center mb-12">
        <h1 id="page-title" 
            class="text-4xl md:text-6xl font-extrabold text-gray-800 opacity-0"
            style="color: var(--accent-color);"
        >
            CSS & Web Dev Flash Review
        </h1>
        <p class="text-gray-500 mt-2 text-lg">Hover over the cards to reveal the answers using a creative drop-down transition.</p>
    </header>

    <!-- Flashcard Grid Container (8 Cards) -->
    <main class="grid grid-cols-1 sm:grid-cols-2 lg:grid-cols-4 gap-6 md:gap-8 max-w-7xl mx-auto">

        <!-- Card 1: CSS Term -->
        <div class="flashcard rounded-xl p-6 cursor-pointer">
            <div class="question-text">
                <h3 class="text-xl font-bold mb-2 text-white">1. What does CSS stand for?</h3>
            </div>
            <div class="answer-content">
                <p class="text-gray-300">Cascading Style Sheets. It describes how HTML elements are to be displayed on screen, paper, or in other media.</p>
            </div>
        </div>

        <!-- Card 2: Box Model -->
        <div class="flashcard rounded-xl p-6 cursor-pointer">
            <div class="question-text">
                <h3 class="text-xl font-bold mb-2 text-white">2. What is the CSS Box Model?</h3>
            </div>
            <div class="answer-content">
                <p class="text-gray-300">A box wrapped around every HTML element. It consists of the content, padding, border, and margins, from inside to outside.</p>
            </div>
        </div>

        <!-- Card 3: Z-index -->
        <div class="flashcard rounded-xl p-6 cursor-pointer">
            <div class="question-text">
                <h3 class="text-xl font-bold mb-2 text-white">3. Explain the 'Z-index' property.</h3>
            </div>
            <div class="answer-content">
                <p class="text-gray-300">It specifies the stack order of an element. A higher index positions the element closer to the viewer (in front) on the Z-axis.</p>
            </div>
        </div>

        <!-- Card 4: Flexbox -->
        <div class="flashcard rounded-xl p-6 cursor-pointer">
            <div class="question-text">
                <h3 class="text-xl font-bold mb-2 text-white">4. What is 'Flexbox'?</h3>
            </div>
            <div class="answer-content">
                <p class="text-gray-300">A one-dimensional layout method designed to help arrange and distribute space among items in a container, even when their size is unknown or dynamic.</p>
            </div>
        </div>
        
        <!-- Card 5: Units -->
        <div class="flashcard rounded-xl p-6 cursor-pointer">
            <div class="question-text">
                <h3 class="text-xl font-bold mb-2 text-white">5. Difference between 'em' and 'rem'?</h3>
            </div>
            <div class="answer-content">
                <p class="text-gray-300">'em' is relative to the parent element's font-size. 'rem' (root em) is relative to the root (<span class="font-mono text-sm text-yellow-400">&lt;html&gt;</span>) element's font-size, which helps prevent compounding size issues.</p>
            </div>
        </div>

        <!-- Card 6: Grid -->
        <div class="flashcard rounded-xl p-6 cursor-pointer">
            <div class="question-text">
                <h3 class="text-xl font-bold mb-2 text-white">6. What is the primary function of CSS Grid?</h3>
            </div>
            <div class="answer-content">
                <p class="text-gray-300">It's a two-dimensional layout system that allows developers to control rows and columns, offering greater precision over complex layouts than Flexbox.</p>
            </div>
        </div>

        <!-- Card 7: Media Queries -->
        <div class="flashcard rounded-xl p-6 cursor-pointer">
            <div class="question-text">
                <h3 class="text-xl font-bold mb-2 text-white">7. What is the core use of a Media Query?</h3>
            </div>
            <div class="answer-content">
                <p class="text-gray-300">To apply different CSS styles based on a device's characteristics (like screen width or resolution), which is fundamental for responsive design.</p>
            </div>
        </div>

        <!-- Card 8: Specificity -->
        <div class="flashcard rounded-xl p-6 cursor-pointer">
            <div class="question-text">
                <h3 class="text-xl font-bold mb-2 text-white">8. What is CSS Specificity?</h3>
            </div>
            <div class="answer-content">
                <p class="text-gray-300">The algorithm that determines which CSS declaration applies to an element when multiple rules target it. ID selectors have higher specificity than class selectors.</p>
            </div>
        </div>

    </main>

</body>
</html>
