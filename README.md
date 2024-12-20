

<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Knot Explorer</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            margin: 20px;
        }
        .category, .knot {
            margin-bottom: 20px;
        }
        img {
            max-width: 300px;
            height: auto;
            display: block;
            margin-top: 20px;
        }
    </style>
</head>
<body>
    <h1>Welcome to the Knot Explorer!</h1>
    <div class="category">
        <label for="categories">Choose a category:</label>
        <select id="categories">
            <option value="">Select a category</option>
            <option value="1">Basic Knots</option>
            <option value="2">Climbing Knots</option>
            <option value="3">Sailing Knots</option>
            <option value="4">Decorative Knots</option>
            <option value="5">Fishing Knots</option>
            <option value="6">Utility Knots</option>
            <option value="7">Specialized Knots</option>
        </select>
    </div>

    <div class="knot" id="knot-options" style="display: none;">
        <label for="knots">Choose a knot:</label>
        <select id="knots">
            <option value="">Select a knot</option>
        </select>
    </div>

    <div id="result" style="display: none;">
        <h3>Knot Information</h3>
        <img id="knot-image" src="" alt="Knot image">
        <p id="description"></p>
    </div>

    <script>
        const categories = {
            1: ["Square Knot", "Bowline Knot", "Sheet Bend Knot", "Clove Hitch Knot"],
            2: ["Figure Eight Knot", "Alpine Butterfly Knot", "Prusik Knot", "Water Knot"],
            3: ["Rolling Hitch Knot", "Clove Hitch Knot", "Reef Knot", "Bowline Knot"],
            4: ["Monkey's Fist Knot", "Turk's Head Knot", "Matthew Walker Knot", "Carrick Bend Knot"],
            5: ["Blood Knot", "Fisherman's Knot", "Improved Clinch Knot", "Barrel Knot"],
            6: ["Trucker's Hitch Knot", "Taut-Line Hitch Knot", "Round Turn and Two Half Hitches", "Timber Hitch Knot"],
            7: ["Eldridge Knot", "Gordian Knot", "Klemheist Knot", "Bends"]
        };

        const knotImages = {
            "Square Knot": "https://example.com/square-knot.jpg",
            "Bowline Knot": "https://example.com/bowline-knot.jpg",
            "Sheet Bend Knot": "https://example.com/sheet-bend-knot.jpg",
            "Clove Hitch Knot": "https://example.com/clove-hitch-knot.jpg",
            "Figure Eight Knot": "https://example.com/figure-eight-knot.jpg",
            // Add more knot image URLs here
        };

        const knotDescriptions = {
            "Square Knot": "A simple binding knot used to secure two ends of a rope together.",
            "Bowline Knot": "Creates a fixed loop at the end of a rope. It's strong and does not slip.",
            "Sheet Bend Knot": "A knot used for joining two ropes of different sizes.",
            "Clove Hitch Knot": "A simple knot for temporarily fastening a rope to a post.",
            "Figure Eight Knot": "A strong knot used in climbing to secure the rope.",
            // Add more knot descriptions here
        };

        document.getElementById('categories').addEventListener('change', function() {
            const category = this.value;
            const knotSelect = document.getElementById('knots');

            if (category) {
                knotSelect.innerHTML = '<option value="">Select a knot</option>';
                categories[category].forEach(knot => {
                    const option = document.createElement('option');
                    option.value = knot;
                    option.textContent = knot;
                    knotSelect.appendChild(option);
                });
                document.getElementById('knot-options').style.display = 'block';
            } else {
                document.getElementById('knot-options').style.display = 'none';
                document.getElementById('result').style.display = 'none';
            }
        });

        document.getElementById('knots').addEventListener('change', function() {
            const knot = this.value;

            if (knot) {
                document.getElementById('knot-image').src = knotImages[knot] || 'https://via.placeholder.com/300';
                document.getElementById('knot-image').alt = knot;
                document.getElementById('description').textContent = knotDescriptions[knot] || 'Description not available.';
                document.getElementById('result').style.display = 'block';
            } else {
                document.getElementById('result').style.display = 'none';
            }
        });
    </script>
</body>
</html>

