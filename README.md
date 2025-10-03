## Formula 1 2D — Pygame

A lightweight 2D Formula 1 racing game built with Pygame. Drive an F1 car around a top‑down track, avoid going off‑track, and chase lap times. Designed to be simple to set up and extend as you add cars, AI opponents, new tracks, and game modes.

### Key Features (initial scope)
- **Top‑down driving**: Smooth 2D movement with acceleration, braking, and turning.
- **Lap timing**: Start/finish line detection and best‑lap tracking.
- **Track limits**: Slowdowns or penalties when off‑track (rumble/grass).
- **Basic HUD**: Speed, gear/engine state (optional), lap counter, best/current lap.
- **Keyboard controls**: Ready to play without a controller.

### Planned Enhancements (roadmap)
- **AI cars** with simple racing lines and avoidance.
- **Multiple tracks** with different difficulty and surface friction.
- **Ghost car** replay of your best lap.
- **Game modes**: Time Trial, Quick Race, Championship.
- **Controller support** and customizable key bindings.
- **Audio**: Engine pitch, tire squeal, off‑track rumble.
- **Polish**: Main menu, pause screen, results screen, and save data.

## Controls (default)
- **Up / W**: Throttle
- **Down / S**: Brake/Reverse (at low speed)
- **Left / A**: Steer left
- **Right / D**: Steer right
- **Space**: Handbrake (optional drift)
- **Esc**: Pause/Quit

## Tech Stack
- **Language**: Python 3.10+
- **Engine/Library**: Pygame (2.1+)
- **Assets**: Simple PNG sprites for car and track; TTF fonts for HUD

## Getting Started
### Prerequisites
- Python 3.10+ installed (`python --version`)
- `pip` available (`python -m pip --version`)

### Setup
```bash
# 1) Create and activate a virtual environment (recommended)
python -m venv .venv
source .venv/bin/activate   # Windows: .venv\Scripts\activate

# 2) Install dependencies
python -m pip install --upgrade pip
pip install pygame
```

### Run the game
```bash
python main.py
```

If `main.py` does not exist yet, create a starter file and verify Pygame opens a window:
```python
import pygame

pygame.init()
screen = pygame.display.set_mode((960, 540))
pygame.display.set_caption("Formula 1 2D — Pygame")
clock = pygame.time.Clock()

running = True
while running:
    for event in pygame.event.get():
        if event.type == pygame.QUIT:
            running = False

    screen.fill((20, 20, 20))
    pygame.display.flip()
    clock.tick(60)

pygame.quit()
```

## Suggested Project Structure
```
formula1_pygame/
├─ assets/
│  ├─ cars/              # car sprites
│  ├─ tracks/            # track images and metadata (start line, checkpoints)
│  └─ fonts/
├─ game/
│  ├─ core/              # engine: loop, scenes, timing
│  ├─ physics/           # movement, collision, friction
│  ├─ entities/          # Car, Track, Checkpoint, HUD
│  ├─ ai/                # simple racing line + avoidance (future)
│  └─ utils/             # helpers (math, config, resources)
├─ main.py               # entry point, scene bootstrapping
└─ README.md
```

## Design Notes
- Use a **fixed timestep** for physics (e.g., 60 FPS) to keep handling consistent.
- Represent car state with position, heading (radians), velocity, and angular velocity.
- Apply forces for throttle and braking; apply lateral friction to limit sliding.
- Track limits can be implemented by sampling pixel colors from a **track mask** or by **polygon zones** with different friction.
- Lap timing: require passing through a series of checkpoints before a lap is valid.

## Contributing
1. Fork the repo and create a feature branch.
2. Keep functions small and focused; prefer clear naming over comments.
3. Open a PR describing the change, include screenshots/GIFs if UI behavior changes.

## License
MIT License. You may use, modify, and distribute with attribution. Replace or update this section if you choose a different license.

## Acknowledgements
- Pygame community and docs
- Real‑world F1 telemetry and racing lines for inspiration


