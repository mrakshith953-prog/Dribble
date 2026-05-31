# Project Responsive Web Design using Bootstrap
## Date:31-05-2026

## AIM:
To create a simplified clone of Dribbble (https://dribbble.com/) landing page.


## DESIGN STEPS:

### Step 1:
Clone the repository from GitHub.

### Step 2:
Create Django Admin project.

### Step 3:
Create a New App under the Django Admin project.

### Step 4:
Insert the necessary CSS and JavaScript files as external in order to use Bootstrap.

### Step 5:
Create a HTML file and include the needed Bootstrap components.

### Step 6:
Publish the website in the LocalHost.

## PROGRAM :
```
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Dribbble Clone - Modern Interactive</title>
    <script src="https://cdn.tailwindcss.com"></script>
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">
    <script>
        // Tailwind Custom Configuration
        tailwind.config = {
            theme: {
                extend: {
                    colors: {
                        brandPink: '#ea4c89',
                        brandDark: '#0d0c22',
                        brandGray: '#6e6d7a',
                        brandLight: '#f8f7f4'
                    }
                }
            }
        }
    </script>
</head>
<body class="bg-white text-brandDark antialiased">

    <nav class="sticky top-0 z-50 flex items-center justify-between h-20 px-6 bg-white border-b border-gray-200 md:px-12">
        <div class="flex items-center gap-8">
            <a href="#" class="font-serif text-2xl font-bold tracking-tighter italic">dribbble</a>
            <ul class="hidden lg:flex items-center gap-6 text-sm font-semibold text-brandGray">
                <li><a href="#" class="hover:text-brandDark transition">Explore</a></li>
                <li><a href="#" class="hover:text-brandDark transition">Find Designers</a></li>
                <li><a href="#" class="hover:text-brandDark transition">Inspiration</a></li>
                <li><a href="#" class="hover:text-brandDark transition">Jobs</a></li>
                <li><a href="#" class="hover:text-brandDark transition">Go Pro</a></li>
            </ul>
        </div>
        
        <div class="flex items-center gap-5">
            <div class="relative hidden sm:block">
                <i class="fa-solid fa-magnifying-glass absolute left-3 top-1/2 -translate-y-1/2 text-brandGray text-sm"></i>
                <input type="text" placeholder="Search..." class="w-40 focus:w-56 bg-gray-100 focus:bg-white border border-transparent focus:border-brandPink/50 rounded-full py-2 pl-9 pr-4 text-sm outline-none transition-all duration-300">
            </div>
            <a href="#" class="text-sm font-semibold text-brandGray hover:text-brandDark">Log in</a>
            <a href="#" class="bg-brandDark hover:bg-gray-800 text-white text-sm font-semibold px-5 py-2.5 rounded-xl transition">Sign up</a>
        </div>
    </nav>

    <section class="bg-brandDark text-white text-center py-20 px-6 flex flex-direction flex-col items-center justify-center">
        <span class="bg-pink-500/10 text-brandPink text-xs font-bold uppercase tracking-widest px-3 py-1 rounded-full mb-4">Over 3 million designers</span>
        <h1 class="text-4xl md:text-6xl font-bold max-w-3xl tracking-tight leading-tight mb-6">Discover the world’s top designers & creatives</h1>
        <p class="text-gray-400 text-lg md:text-xl max-w-xl mb-8 font-light">Dribbble is the leading destination to find & showcase creative work and home to the world's best design professionals.</p>
        
        <div class="w-full max-w-2xl bg-white rounded-full p-2 flex items-center shadow-xl">
            <i class="fa-solid fa-magnifying-glass text-gray-400 ml-4 mr-2"></i>
            <input type="text" placeholder="Search creative work..." class="w-full text-brandDark py-2 px-2 outline-none text-base">
            <button class="bg-brandPink hover:bg-pink-600 text-white px-6 py-3 rounded-full font-semibold text-sm transition shrink-0">Search</button>
        </div>
    </section>

    <div class="flex items-center justify-between px-6 md:px-12 py-8 border-b border-gray-100">
        <ul id="category-list" class="flex items-center gap-3 overflow-x-auto no-scrollbar max-w-[75%]">
            <li><button onclick="changeCategory(this)" class="cat-btn bg-brandDark text-white text-sm font-semibold px-4 py-2 rounded-xl transition whitespace-nowrap">Popular</button></li>
            <li><button onclick="changeCategory(this)" class="cat-btn text-brandGray hover:bg-gray-100 hover:text-brandDark text-sm font-semibold px-4 py-2 rounded-xl transition whitespace-nowrap">Typography</button></li>
            <li><button onclick="changeCategory(this)" class="cat-btn text-brandGray hover:bg-gray-100 hover:text-brandDark text-sm font-semibold px-4 py-2 rounded-xl transition whitespace-nowrap">Product Design</button></li>
            <li><button onclick="changeCategory(this)" class="cat-btn text-brandGray hover:bg-gray-100 hover:text-brandDark text-sm font-semibold px-4 py-2 rounded-xl transition whitespace-nowrap">Illustration</button></li>
            <li><button onclick="changeCategory(this)" class="cat-btn text-brandGray hover:bg-gray-100 hover:text-brandDark text-sm font-semibold px-4 py-2 rounded-xl transition whitespace-nowrap">Mobile</button></li>
            <li><button onclick="changeCategory(this)" class="cat-btn text-brandGray hover:bg-gray-100 hover:text-brandDark text-sm font-semibold px-4 py-2 rounded-xl transition whitespace-nowrap">Web Design</button></li>
        </ul>

        <button class="flex items-center gap-2 border border-gray-200 hover:border-brandDark text-sm font-semibold px-4 py-2 rounded-xl transition shrink-0">
            <i class="fa-solid fa-sliders text-xs"></i> Filters
        </button>
    </div>

    <main class="px-6 md:px-12 py-10">
        <div id="shots-container" class="grid grid-cols-1 sm:grid-cols-2 md:grid-cols-3 xl:grid-cols-4 gap-8">
            </div>
    </main>

    <script>
        // Mock Data Array representing individual Dribbble "Shots"
        const shotsData = [
            { id: 1, title: 'Crypto Wallet Interface', designer: 'Sarah Jenkins', pro: true, team: false, likes: 142, views: '10.4k', avatar: 'https://i.pravatar.cc/150?img=32', image: 'https://picsum.photos/seed/wallet/600/450' },
            { id: 2, title: 'Smart Home Mobile UX', designer: 'Oleg Polovko', pro: false, team: true, likes: 95, views: '4.2k', avatar: 'https://i.pravatar.cc/150?img=12', image: 'https://picsum.photos/seed/smarthome/600/450' },
            { id: 3, title: 'Abstract 3D Shapes', designer: 'Studio Shape', pro: true, team: false, likes: 310, views: '28.1k', avatar: 'https://i.pravatar.cc/150?img=47', image: 'https://picsum.photos/seed/3d/600/450' },
            { id: 4, title: 'Minimalist Coffee Brand', designer: 'Emma Watson', pro: false, team: false, likes: 64, views: '3.1k', avatar: 'https://i.pravatar.cc/150?img=44', image: 'https://picsum.photos/seed/coffee/600/450' },
            { id: 5, title: 'Neomorphic Fitness Tracker', designer: 'David K.', pro: true, team: false, likes: 188, views: '15.6k', avatar: 'https://i.pravatar.cc/150?img=60', image: 'https://picsum.photos/seed/fitness/600/450' },
            { id: 6, title: 'SaaS Analytics Dashboard', designer: 'Pixel Kraft', pro: false, team: true, likes: 245, views: '19.9k', avatar: 'https://i.pravatar.cc/150?img=68', image: 'https://picsum.photos/seed/dashboard/600/450' },
            { id: 7, title: 'Cyberpunk Vector Art', designer: 'NeoVibe', pro: true, team: false, likes: 412, views: '32.4k', avatar: 'https://i.pravatar.cc/150?img=11', image: 'https://picsum.photos/seed/cyber/600/450' },
            { id: 8, title: 'Travel Booking Concept', designer: 'Clara Oswald', pro: false, team: false, likes: 73, views: '5.0k', avatar: 'https://i.pravatar.cc/150?img=52', image: 'https://picsum.photos/seed/travel/600/450' }
        ];

        // Function to inject cards into the HTML container
        function renderShots() {
            const container = document.getElementById('shots-container');
            container.innerHTML = shotsData.map(shot => `
                <div class="group flex flex-col cursor-pointer">
                    <div class="relative aspect-[4/3] rounded-xl overflow-hidden bg-gray-100 shadow-sm">
                        <img src="${shot.image}" alt="${shot.title}" class="w-full h-full object-cover">
                        
                        <div class="absolute inset-0 bg-gradient-to-t from-black/60 via-black/0 to-black/0 p-4 flex items-end justify-between opacity-0 group-hover:opacity-100 transition-opacity duration-200">
                            <span class="text-white font-semibold text-sm truncate max-w-[60%]">${shot.title}</span>
                            <div class="flex gap-2">
                                <button onclick="event.stopPropagation();" class="w-8 h-8 rounded-lg bg-white hover:bg-brandPink text-brandDark hover:text-white flex items-center justify-center transition text-xs shadow-md">
                                    <i class="fa-solid fa-bookmark"></i>
                                </button>
                                <button onclick="toggleLike(event, ${shot.id})" class="w-8 h-8 rounded-lg bg-white hover:bg-brandPink text-brandDark hover:text-white flex items-center justify-center transition text-xs shadow-md">
                                    <i class="fa-solid fa-heart"></i>
                                </button>
                            </div>
                        </div>
                    </div>

                    <div class="flex items-center justify-between mt-3 px-1">
                        <div class="flex items-center gap-2">
                            <img src="${shot.avatar}" alt="Avatar" class="w-6 h-6 rounded-full object-cover">
                            <span class="text-sm font-medium text-brandDark hover:underline truncate max-w-[110px]">${shot.designer}</span>
                            ${shot.pro ? '<span class="bg-brandPink text-[10px] font-bold text-white px-1.5 py-0.5 rounded uppercase tracking-wide">Pro</span>' : ''}
                            ${shot.team ? '<span class="bg-gray-400 text-[10px] font-bold text-white px-1.5 py-0.5 rounded uppercase tracking-wide">Team</span>' : ''}
                        </div>
                        <div class="flex items-center gap-3 text-xs font-bold text-brandGray">
                            <span class="flex items-center gap-1 hover:text-brandPink transition">
                                <i class="fa-solid fa-heart"></i> <span id="like-count-${shot.id}">${shot.likes}</span>
                            </span>
                            <span class="flex items-center gap-1">
                                <i class="fa-solid fa-eye"></i> ${shot.views}
                            </span>
                        </div>
                    </div>
                </div>
            `).join('');
        }

        // Functional Mock Feature: Increment likes on click
        function toggleLike(event, id) {
            event.stopPropagation(); // Avoid triggering card links
            const targetShot = shotsData.find(s => s.id === id);
            if (targetShot) {
                targetShot.likes++;
                document.getElementById(`like-count-${id}`).innerText = targetShot.likes;
            }
        }

        // Category Selection UI Interaction
        function changeCategory(element) {
            document.querySelectorAll('.cat-btn').forEach(btn => {
                btn.className = "cat-btn text-brandGray hover:bg-gray-100 hover:text-brandDark text-sm font-semibold px-4 py-2 rounded-xl transition whitespace-nowrap";
            });
            element.className = "cat-btn bg-brandDark text-white text-sm font-semibold px-4 py-2 rounded-xl transition whitespace-nowrap";
        }

        // Initial setup execution
        renderShots();
    </script>

    <style>
        .no-scrollbar::-webkit-scrollbar { display: none; }
        .no-scrollbar { -ms-overflow-style: none; scrollbar-width: none; }
    </style>
</body>
</html>
```

## OUTPUT:

<img width="1899" height="875" alt="Screenshot 2026-05-31 204642" src="https://github.com/user-attachments/assets/24fc84d6-8a2e-48fb-8cdd-ec2954ff2da3" />
<img width="1902" height="910" alt="Screenshot 2026-05-31 204711" src="https://github.com/user-attachments/assets/89a8d3d5-bd73-45fb-afc2-7976c60fd256" />



## RESULT:
The Project for responsive web design using Bootstrap is completed successfully.
