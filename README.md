# PAS_DZ_01

## Opis
Matija Pongračić: Projektiranje autonomnih sustava - DZ 01

## Zahtjevi
- ROS 2 instaliran na sustavu
- colcon build alat za izgradnju ROS 2 workspace-a
- Git za preuzimanje repozitorija

## Instalacija i pokretanje

### Kreiranje ROS 2 workspace-a
U terminalu pokrenuti sljedeće naredbe za kreiranje ROS2 workspace-a.
```bash
mkdir -p ros2_ws/src
cd ros2_ws/src
```

### Preuzimanje repozitorija
Klonirati repozitorij s GitHub-a u `src` direktorij.
```bash
git clone https://github.com/MatijaPongracic/PAS_DZ_01.git
```

### Buildanje projekta i postavljanje okruženja
Vratiti se u root direktorij workspace-a, izgraditi workspace i source-ati postavke.
```bash
cd ..
colcon build
source install/setup.bash
```

### (1) Pokretanje launch datoteke za vizualizaciju i upravljanje
Za vizualizaciju robota i upravljanje pozicijama zglobova putem GUI-a pokrenuti:
```bash
ros2 launch my_robot_description display.launch.py
```

### (2) Pokretanje launch datoteke za pokretanje robota s controllerima
Zaustaviti prošlu launch datoteku pomoću `ctrl + C`.

Pokrenuti launch datoteku:
```bash
ros2 launch my_robot_bringup my_robot.launch.py
```

Otvoriti novi terminal i source-ati postavke:
```bash
source install/setup.bash
```

Pokretanjem naredbe
```bash
ros2 control list_controllers
```
vidljivo je da su učitana 3 controllera, od kojih 2 traže input.

Kod pokretanja launch datoteke `joint_trajectoy_controller` je aktivan, a `forward_position_controller` je neaktivan. U svakom trenutku samo jedan od njih smije biti aktivan.


### (3) Pokretanje launch datoteke za objavljuvanje pozicija na joint_trajectory_controller
U istom terminalu (drugom) pokrenuti:
```bash
ros2 launch my_robot_bringup run_joint_trajectory_controller.launch.py
```

Robotu se svakih 6 sekundi šalje naredba za postizanje nove konfiguracije, što je vidljivo u RViz-vizualizaciji.

### (4) Pokretanje launch datoteke za objavljuvanje pozicija na forward_position_controller
Zaustaviti prošlu launch datoteku pomoću `ctrl + C`.

Prije pokretanja nove launch datoteke potrebno je promijeniti aktivni controller pomoću naredbe:
```bash
ros2 control switch_controllers --deactivate joint_trajectory_position_controller --activate forward_position_controller
```

Ponovnim pokretanjem naredbe `ros2 control list_controllers` vidljivo je da se aktivni controller promijenio.

Launch datoteka za objavljivanje na novi controller pokreće se pomoću naredbe:
```bash
ros2 launch my_robot_bringup run_forward_position_controller.launch.py
```

Za ponovnu aktivaciju prethodnog controllera, pokrenuti naredbu:
```bash
ros2 control switch_controllers --deactivate forward_position_controller --activate joint_trajectory_position_controller 
```
