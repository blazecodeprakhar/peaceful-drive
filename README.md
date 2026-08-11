🚗 Peaceful Drive

A relaxing browser-based driving game built with HTML5 Canvas, CSS, and vanilla JavaScript.

Drive through a procedurally generated countryside with winding roads, traffic, changing weather, dynamic time of day, engine audio, fuel, vehicle health, and a mini-map.

🎮 Features
🚗 Smooth driving system
🛣️ Procedurally generated road environment
🌄 Mountains and countryside scenery
🌲 Trees, rocks, flowers, and other roadside objects
🚦 AI traffic vehicles
🌤️ Dynamic day/night cycle
🌧️ Dynamic weather
Clear
Cloudy
Rain
🌅 Sunrise and sunset colors
🗺️ Mini-map
⛽ Fuel system
❤️ Vehicle health system
💥 Traffic collision detection
🎵 Procedural engine audio using Web Audio API
📱 Mobile touch controls
🖥️ Fullscreen mode
⏸️ Pause/resume system
💾 Local high-score/distance saving
🎥 Third-person driving camera
🛣️ Vehicle positioned on the road
✨ Canvas-based visual effects
📳 Camera shake after collisions
🕹️ Controls
Desktop
Key	Action
W / ↑	Accelerate
S / ↓	Brake / Reverse
A / ←	Steer left
D / →	Steer right
SPACE	Handbrake
ESC	Pause
Mobile

Use the on-screen controls:

◀ — Steer left
▶ — Steer right
▲ — Accelerate
▼ — Brake
📁 Project Structure

The project is designed as a simple single-file web game:

peaceful-drive/
│
├── index.html
└── README.md

index.html

Contains:

Game HTML
HUD
Menu screens
CSS styling
Canvas rendering
Driving physics
Traffic system
Weather system
World generation
Audio system
Mobile controls
Mini-map
Game loop
🚀 Getting Started

No framework or build system is required.

1. Download the project

Clone the repository:

git clone YOUR_REPOSITORY_URL


Or download the project as a ZIP file.

2. Open the project

Open the project folder and launch:

index.html


You can also run it using a local development server.

For example, with VS Code, install Live Server and open index.html using Live Server.

3. Start driving

Click:

START DRIVING


Then use the keyboard or mobile controls.

🌐 Browser Support

The game uses standard browser technologies:

HTML5
CSS3
JavaScript
Canvas 2D API
Web Audio API
Local Storage
Fullscreen API

Modern versions of the following browsers should work:

Google Chrome
Microsoft Edge
Mozilla Firefox
Safari

For the best performance, use a modern Chromium-based browser.

🧠 How the Game Works
Canvas Rendering

The game uses an HTML5 <canvas> as its primary rendering surface.

The world is rendered every frame using JavaScript.

The rendering pipeline includes:

Sky
 ↓
Sun
 ↓
Clouds
 ↓
Mountains
 ↓
Ground
 ↓
Road
 ↓
Roadside scenery
 ↓
Traffic
 ↓
Player vehicle
 ↓
Weather effects
 ↓
HUD


This creates the illusion of a 3D driving environment while using a 2D Canvas renderer.

🛣️ Road System

The road is generated dynamically using perspective projection.

Objects become:

smaller near the horizon
larger as they approach the player
positioned according to their distance from the camera

The road also uses changing curves to create a winding countryside driving experience.

Road elements include:

Asphalt
Yellow road edges
White lane markings
Road perspective
Curves
Roadside scenery
🚗 Driving System

The vehicle has several basic physics properties:

const player = {
    speed: 0,
    maxSpeed: 215,
    acceleration: 115,
    braking: 190,
    friction: 35,
    steering: 1.8
};


The driving system calculates:

Acceleration
Braking
Friction
Steering
Speed
Lateral movement
Handbrake behavior
Road boundaries

The vehicle is restricted to the road area so it does not freely move across the entire environment.

🎥 Camera

The game uses a third-person driving perspective.

The player vehicle is rendered in the lower part of the screen while the road expands toward the camera to create depth.

The camera can be enhanced further with:

Camera follow smoothing
Steering-based camera rotation
Speed-based camera FOV
Suspension movement
Camera bounce
Collision shake
Road curvature perspective
Dynamic camera height
🚦 Traffic

Traffic vehicles are generated procedurally.

Each vehicle receives:

Random color
Random speed
Lane position
Distance from the player

Example:

createTrafficCar(distance)


Traffic vehicles move relative to the player's speed.

If the player gets too close to another vehicle, collision detection is performed.

💥 Collision System

When the player's vehicle hits traffic:

Vehicle health decreases
Player speed decreases
Camera shake occurs
Traffic vehicle is moved away
The journey can end if health reaches zero

Example:

state.health -= 8;
player.speed *= 0.65;
state.shake = 10;

⛽ Fuel System

Fuel gradually decreases while driving.

Fuel consumption depends partly on vehicle speed.

When fuel reaches zero:

The journey ends.


The remaining distance is recorded.

❤️ Vehicle Health

The vehicle begins with:

100% health


Collisions reduce health.

The HUD displays the current vehicle condition using a progress bar.

🌦️ Weather System

The weather can automatically change during the drive.

Available weather states:

CLEAR
CLOUDY
RAIN


Rain adds animated rainfall across the screen.

The weather also works with the dynamic environment and can be expanded with:

Wet roads
Reflections
Fog
Puddles
Thunder
Lightning
Reduced visibility
🌅 Dynamic Time

The game contains a simulated 24-hour clock.

The sky changes depending on the current time.

Different periods include:

Morning
Day
Sunset
Night


The sun moves across the sky and the colors transition between different times of day.

🎵 Engine Audio

The game generates engine audio directly in the browser using the Web Audio API.

The engine pitch changes based on vehicle speed.

For example:

engineOscillator.frequency.value =
    55 + speedRatio * 145;


This allows the engine sound to dynamically respond to acceleration.

🗺️ Mini-map

A small map is displayed in the upper-right corner.

It shows:

Road
Player position
Traffic
Surrounding area
Water

The mini-map is rendered on a separate canvas.

💾 Saved Distance

The game stores the player's best driving distance using browser Local Storage.

The saved value is stored under:

peacefulDriveBest


This means the best distance remains available after refreshing the browser.

📱 Mobile Support

The game includes touch controls for mobile devices.

The interface automatically changes at smaller screen sizes using CSS media queries.

Mobile users receive:

◀   ▶          ▼   ▲


for steering, braking, and acceleration.

🖥️ Fullscreen

The game supports browser fullscreen mode through the Fullscreen API.

Click:

FULLSCREEN


from the main menu to enter fullscreen.

⚡ Performance

The game uses requestAnimationFrame() for rendering:

requestAnimationFrame(loop);


The update loop limits the maximum delta time to prevent large physics jumps after frame drops.

const dt = Math.min(
    0.05,
    (now - state.lastTime) / 1000
);


For better performance on low-end devices, the following improvements can be added:

Object pooling
Reduced scenery count
Lower-resolution rendering
Distance-based object culling
Offscreen canvas rendering
Sprite caching
Particle pooling
🔧 Customization