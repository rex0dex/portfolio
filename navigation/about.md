---
layout: post
title: About
permalink: /about/
comments: true
---

## As a conversation Starter

Here are the places that made me — where I live, where my family is from, and where I have been. 

<comment>
Flags are made using Wikipedia images
</comment>

<style>
    /* Style looks pretty compact, 
       - grid-container and grid-item are referenced the code 
    */
    .grid-container {
        display: grid;
        grid-template-columns: repeat(auto-fill, minmax(150px, 1fr)); /* Dynamic columns */
        gap: 10px;
    }
    .grid-item {
        text-align: center;
    }
    .grid-item img {
        width: 100%;
        height: 100px; /* Fixed height for uniformity */
        object-fit: contain; /* Ensure the image fits within the fixed height */
    }
    .grid-item p {
        margin: 5px 0; /* Add some margin for spacing */
    }

</style>

<!-- This grid_container class is used by CSS styling and the id is used by JavaScript connection -->
<div class="grid-container" id="grid_container">
    <!-- content will be added here by JavaScript -->
</div>

<script>
    // 1. Make a connection to the HTML container defined in the HTML div
    var container = document.getElementById("grid_container"); // This container connects to the HTML div

    // 2. Define a JavaScript object for our http source and our data rows for the Living in the World grid
    var http_source = "https://upload.wikimedia.org/wikipedia/commons/";
    var living_in_the_world = [
        {"flag": "0/01/Flag_of_California.svg", "greeting": "Hey", "description": "California - forever"},
        {"flag": "4/41/Flag_of_India.svg", "greeting": "Namaste", "description": "India - frequently visits"},
        {"flag": "8/88/Flag_of_Australia_%28converted%29.svg", "greeting": "G'day, mate!", "description": "Australia, visited my uncle once"},
        {"flag": "4/48/Flag_of_Singapore.svg", "greeting": "Hello", "description": "Singapore, visited on the way to india (family lives there)"},
    ];

    // 3a. Consider how to update style count for size of container
    // The grid-template-columns has been defined as dynamic with auto-fill and minmax

    // 3b. Build grid items inside of our container for each row of data
    for (const location of living_in_the_world) {
        // Create a "div" with "class grid-item" for each row
        var gridItem = document.createElement("div");
        gridItem.className = "grid-item";  // This class name connects the gridItem to the CSS style elements
        // Add "img" HTML tag for the flag
        var img = document.createElement("img");
        img.src = http_source + location.flag; // concatenate the source and flag
        img.alt = location.flag + " Flag"; // add alt text for accessibility

        // Add "p" HTML tag for the description
        var description = document.createElement("p");
        description.textContent = location.description; // extract the description

        // Add "p" HTML tag for the greeting
        var greeting = document.createElement("p");
        greeting.textContent = location.greeting;  // extract the greeting

        // Append img and p HTML  tags to the grid item DIV
        gridItem.appendChild(img);
        gridItem.appendChild(description);
        gridItem.appendChild(greeting);

        // Append the grid item DIV to the container DIV
        container.appendChild(gridItem);
    }
</script>


### Journey through School

Every school I have gone to has been in Poway Unified, so I have basically grown up with the same group of friends.

- 🎒 **Stone Ranch Elementary** — where it all started, TK through 5th grade
- 🏫 **Oak Valley Middle School** — 6th through 8th grade, first real taste of computers and coding
- 🏆 **Del Norte High School** — Class of '29, currently a sophomore
- 💻 **Computer Science @ Del Norte** — the class this whole portfolio is being built for

### On the Court

🏸 I play **badminton for the Del Norte team**. It looks easy until you actually try to return a smash, the whole game happens in a space smaller than a tennis court. What I like about it is that it rewards being fast and being smart at the same time; you can beat someone who is stronger than you by putting the bird exactly where they are not.



### At home

When I am not in school or on the court, I am usually watching something or playing something. Here is the lineup.

<comment>
Logos are the real show and game logos, pulled from Wikimedia the same way as the flags above.
</comment>

<style>
    .fandom-grid {
        display: grid;
        grid-template-columns: repeat(auto-fill, minmax(160px, 1fr));
        gap: 28px 20px;
        align-items: center;
    }
    .fandom-grid img {
        width: 100%;
        height: 80px;
        object-fit: contain;                /* letterbox instead of crop, logos are all different shapes */
        transition: transform 0.2s ease;
    }
    .fandom-grid img:hover {
        transform: scale(1.08);
    }
    .fandom-grid img.invert {
        filter: invert(1);                  /* the site skin is dark, so flip all-black logos to white */
    }
</style>

<div class="fandom-grid" id="fandom_grid">
    <!-- content will be added here by JavaScript -->
</div>

<script>
// Wrapped in an IIFE so these names do not collide with the flag script above
(function () {
    // 1. Connect to the HTML container defined in the div
    var fandomContainer = document.getElementById("fandom_grid");

    // 2. Data rows: one logo path plus the name, which is used for the alt text
    // Base is the shared prefix; each row carries its own repo folder after it,
    // because free logos live under "commons/" and non-free ones under "en/".
    var wikimedia = "https://upload.wikimedia.org/wikipedia/";
    var fandoms = [
        {"logo": "commons/2/2f/Stranger_Things_logo.svg",                                               "name": "Stranger Things"},
        {"logo": "en/4/4e/Loki_%28TV_series%29_logo.png",                                               "name": "Loki"},
        {"logo": "commons/6/6c/One_piece_logo.svg",                                                     "name": "One Piece"},
        {"logo": "commons/1/1c/Attack_on_Titan_%28international_anglophone%29_logo.svg",                "name": "Attack on Titan"},
        {"logo": "commons/c/c9/Naruto_logo.svg",                                                        "name": "Naruto"},
        {"logo": "commons/1/1f/Hunter_%C3%97_Hunter_logo.png",                                          "name": "Hunter x Hunter"},
        {"logo": "commons/2/25/Marvel%27s_Spider-Man_2_%282025%29_logo_official_%28SGDB_124347%29.png", "name": "Spider-Man 2"},
        {"logo": "commons/0/0e/FortniteLogo.svg",                                                       "name": "Fortnite", "invert": true},
        {"logo": "commons/6/6c/Roblox_Logo.svg",                                                        "name": "Roblox"},
    ];

    // 3. Build an image inside the container for each row of data
    for (const item of fandoms) {
        // Add "img" HTML tag for the logo
        var logo = document.createElement("img");
        logo.src = wikimedia + item.logo;    // concatenate the source and the logo path
        logo.alt = item.name + " logo";      // the only place the name still appears, for screen readers
        logo.loading = "lazy";               // do not block page load on 9 images
        if (item.invert) {                   // only set on logos that are solid black
            logo.classList.add("invert");
        }

        // Append the img straight to the container, no card wrapper
        fandomContainer.appendChild(logo);
    }
})();
</script>

**The short version of my taste:** long anime where it is over 400 episodes, sci-fi shows with a group of friends at the center, and games I can hop into with those same friends. One Piece and Hunter x Hunter are the shows I love the most. Spider-Man 2 on PS5 is the one I have replayed the most, swinging around that map never gets old.

<comment>
Gallery of Pics, scroll to the right for more ...
</comment>
<div class="image-gallery">
  <img src="{{site.baseurl}}/images/about/IMG_3414.jpeg" alt="Image 1">
  <img src="{{site.baseurl}}/images/about/IMG_3984.jpeg" alt="Image 2">
  <img src="{{site.baseurl}}/images/about/IMG_4274.jpg" alt="Image 3">
  <img src="{{site.baseurl}}/images/about/IMG_4308.jpg" alt="Image 4">
  <img src="{{site.baseurl}}/images/about/IMG_4393.jpeg" alt="Image 5">
  <img src="{{site.baseurl}}/images/about/FullSizeRender.jpg" alt="Image 6">
</div>


