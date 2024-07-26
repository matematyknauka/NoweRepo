import os

# Ścieżka do katalogu lokalnego
local_directory = '/content/drive/MyDrive/ESRGAN_sd_do_hd'
os.chdir(local_directory)

# Zmiana nazwy gałęzi na 'main'
!git branch -M main

# Sprawdzenie obecnych zdalnych repozytoriów
remote_list = !git remote -v

# Sprawdzenie, czy zdalne repozytorium 'origin' istnieje
if 'origin' in remote_list:
    print("Usuwanie zdalnego repozytorium 'origin'")
    !git remote remove origin
else:
    print("Zdalne repozytorium 'origin' nie istnieje. Kontynuowanie...")

# Dodanie nowego zdalnego repozytorium o nazwie 'ESRGAN_sd_do_hd'
repo_url = "https://github.com/matematyknauka/ESRGAN_sd_do_hd.git"
!git remote add ESRGAN_sd_do_hd $repo_url

# Wypychanie gałęzi 'main' do zdalnego repozytorium
!git push -u ESRGAN_sd_do_hd main
