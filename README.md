# grgsm_scanner-GUI
# Create a simple GUI for Gr-GSM Scanner

# Create a GUI for Gr-GSM using Zenity that enables easy control of bands of operation and gain. This GUI also lets you add a session tag / location and stores the collected data as .csv files for ease of use. 

# Identify a suitable data storage location, I created a folder within documents for this:

mkdir ~/Documents/GSM_Survey

sudo chmod 777 ~/Documents/GSM_Survey

# Manually create the files using the details below:

# Use Gedit to create a bash script:

sudo gedit /Documents/GSM_Survey/gsmsurvey.sh

# Copy the following text into the file:

#!/usr/bin/env bash

timestamp=$(date +%Y-%m-%d:%H:%M)

opt1="GSM900"

opt2="DCS1800"

opt3="GSM850"

opt4="PCS1900"

opt5="GSM450"

opt6="GSM480"

opt7="Railway-GSM"

gsmsurvey=$(zenity --list --title "Basic GSM Survey" --radiolist  --column "" --column "" TRUE "$opt1" FALSE "$opt2" FALSE "$opt2" FALSE "$opt4" FALSE "$opt5" FALSE "$opt6" FALSE "$opt7" --height=400 --width=300)

case $gsmsurvey in

$opt1 )

location=$(zenity --entry --title "Location / Session Tag" --text "Enter Session Tag or Location")

gain=$(zenity --entry --title "Gain" --text "Enter RF Gain to apply")

grgsm_scanner -g $gain | tee ~/Documents/GSM_Survey/$location-$opt1-$timestamp.csv | (zenity --progress --pulsate --no-cancel --auto-close --title="GSM Survey" --

text="Conducting $opt1 Survey, please wait")

nautilus ~/Documents/GSM_Survey/

exit;;

$opt2 )

location=$(zenity --entry --title "Location / Session Tag" --text "Enter Session Tag or Location")

gain=$(zenity --entry --title "Gain" --text "Enter RF Gain to apply")

grgsm_scanner --band $opt2 -g $gain | tee ~/Documents/GSM_Survey/$location-$opt2-$timestamp.csv | (zenity --progress --pulsate --no-cancel --auto-close --title="GSM Survey" --text="Conducting $opt2 Survey, please wait")

nautilus ~/Documents/GSM_Survey/

exit;;

$opt3 )

location=$(zenity --entry --title "Location / Session Tag" --text "Enter Session Tag or Location")

gain=$(zenity --entry --title "Gain" --text "Enter RF Gain to apply")

grgsm_scanner --band $opt3 -g $gain | tee ~/Documents/GSM_Survey/$location-$opt3-$timestamp.csv | (zenity --progress --pulsate --no-cancel --auto-close --title="GSM Survey" --text="Conducting $opt3 Survey, please wait")

nautilus ~/Documents/GSM_Survey/

exit;;

$opt4 )

location=$(zenity --entry --title "Location / Session Tag" --text "Enter Session Tag or Location")

gain=$(zenity --entry --title "Gain" --text "Enter RF Gain to apply")

grgsm_scanner --band $opt4 -g $gain | tee ~/Documents/GSM_Survey/$location-$opt4-$timestamp.csv | (zenity --progress --pulsate --no-cancel --auto-close --title="GSM Survey" --text="Conducting $opt4 Survey, please wait")

nautilus ~/Documents/GSM_Survey/

exit;;

$opt5 )

location=$(zenity --entry --title "Location / Session Tag" --text "Enter Session Tag or Location")

gain=$(zenity --entry --title "Gain" --text "Enter RF Gain to apply")

grgsm_scanner --band $opt5 -g $gain | tee ~/Documents/GSM_Survey/$location-$opt5-$timestamp.csv | (zenity --progress --pulsate --no-cancel --auto-close --title="GSM Survey" --text="Conducting $opt5 Survey, please wait")

nautilus ~/Documents/GSM_Survey/

exit;;

$opt6 )

location=$(zenity --entry --title "Location / Session Tag" --text "Enter Session Tag or Location")

gain=$(zenity --entry --title "Gain" --text "Enter RF Gain to apply")

grgsm_scanner --band $opt6 -g $gain | tee ~/Documents/GSM_Survey/$location-$opt6-$timestamp.csv | (zenity --progress --pulsate --no-cancel --auto-close --title="GSM Survey" --text="Conducting $opt6 Survey, please wait")

nautilus ~/Documents/GSM_Survey/

exit;;

$opt7 )

location=$(zenity --entry --title "Location / Session Tag" --text "Enter Session Tag or Location")

gain=$(zenity --entry --title "Gain" --text "Enter RF Gain to apply")

grgsm_scanner --band GSM-R -g $gain | tee ~/Documents/GSM_Survey/$location-$opt7-$timestamp.csv | (zenity --progress --pulsate --no-cancel --auto-close --title="GSM Survey" --text="Conducting $opt7 Survey, please wait")

nautilus ~/Documents/GSM_Survey/

exit;;esac

# Make this file executable:

sudo chmod +x ~/Documents/GSM_Survey/gsmsurvey.sh

# Identify a suitable icon and save in your Pictures folder

# Create a desktop registry file:

sudo gedit /usr/share/applications/survey.desktop

# Add the following text to the file:

# Note use square beackets not rounded here:

(Desktop Entry)

Type=Application

Name=GSM Survey

Categories=Application;GSM

Exec=/home/YOUR USER NAME/Documents/GSM_Survey/gsmsurvey.sh

Icon=/home/YOUR USER NAME/Pictures/icons/YOUR ICON FILE NAME.png

Terminal=true
