# Music starts after sudo reboot, but not at initial power up.
# When audio file plays. It does not play correctly 

Start-up-music-for-Raspberry-Pi
#music plays when headless starts up.
# This is the location of my service file ( /etc/systemd/system/opening_audio.service)
# opening_audio.service
[Unit]
Description=plays Let It Rip when powered on

[Service]
ExecStart=/usr/bin/python /home/Bay/Bookshelf/play_mp3.py
Restart=always
User=Bay

[Install]
WantedBy=multi-user.target

#This is the Program ( Play_mp3.py )

import pygame
import time

pygame.mixer.init()
pygame.mixer.music.load("/home/Bay/Music/letitrip.mp3")
pygame.mixer.music.set_volume(0.5)
time.sleep(3)
pygame.mixer.music.play()
pygame.time.delay(9000)
pygame.mixer.music.stop()
pygame.quit()


