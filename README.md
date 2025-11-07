# PAS_DZ_01

## Opis
Ovaj projekt omogućava vizualizaciju robota i upravljanje pozicijama zglobova putem grafičkog korisničkog sučelja (GUI) koristeći ROS 2 framework.

## Zahtjevi
- ROS 2 instaliran na sustavu
- colcon build alat za izgradnju ROS 2 workspace-a
- Git za preuzimanje repozitorija

## Instalacija i pokretanje

### 1. Kreiranje ROS 2 workspace-a
U terminalu pokrenite sljedeće naredbe za kreiranje workspace-a:
mkdir -p ros2_ws/src
cd ros2_ws/src

### 2. Preuzimanje repozitorija
Klonirajte repozitorij s GitHub-a u `src` direktorij:
git clone https://github.com/MatijaPongracic/PAS_DZ_01.git

### 3. Povratak u root workspace direktorij
Vratite se u root direktorij workspace-a:
cd ..

### 4. Buildanje projekta i postavljanje okruženja
Izgradite workspace i source-ajte postavke:
colcon build
source install/setup.bash

### 5. Pokretanje launch datoteke
Za vizualizaciju robota i upravljanje zglobovima pokrenite:
ros2 launch my_robot_description display.launch.py

### 6. Gašenje launch datoteke
Zaustavite pokrenutu launch datoteku pritiskom na Ctrl+C u terminalu gdje je pokrenuta ili drugim prikladnim načinom.

## Dodatne informacije
- Svaki put kada otvorite novi terminal, potrebno je source-ati workspace s:
source ~/ros2_ws/install/setup.bash

