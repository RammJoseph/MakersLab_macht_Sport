# MakersLab_macht_Sport
Data for Colab

# Beispielcode für die Auswertung des MakersLab-macht_Sport 

# Importieren der benötigten Bibliotheken
import pandas as pd
import matplotlib.pyplot as plt

# Einlesen und darstellen Parcour 1
Parcour1 = pd.read_csv("Parcour1.csv")
Parcour1.columns = ["Zeit", "X", "Y", "Z", "Summe"]

plt.plot(Parcour1["Zeit"], Parcour1["Summe"], label="Parcour 1", color="blue")

# Anpassung Bildgröße / Gitter / Beschriftungen
plt.figure(figsize=(12, 6))
plt.grid()
plt.plot(Parcour1["Zeit"], Parcour1["Summe"], label="Parcour 1", color="blue")
plt.plot(Parcour2["Zeit"], Parcour2["Summe"], label="Parcour 2", color="red")
plt.xlabel("Zeit (s)")
plt.ylabel("Summe Beschleunigung (m/s²)")
plt.title("Vergleich der Parcours")
plt.legend()

# Maximale Werte 
# Maximalwert Parcour 1
max_Parcour1 = Parcour1["Summe"].max()
# Zeitpunkt des Maximalwerts Parcour 1
max_time_Parcour1 = Parcour1.loc[Parcour1["Summe"].idxmax(), "Zeit"]
# Ausgabe des Maximalwerts und des Zeitpunkts
print(f"Maximalwert Parcour 1: {max_Parcour1} m/s² bei {max_time_Parcour1} s")


# Maximalwert Parcour 2
max_Parcour2 = Parcour2["Summe"].max()
# Zeitpunkt des Maximalwerts Parcour 2
max_time_Parcour2 = Parcour2.loc[Parcour2["Summe"].idxmax(), "Zeit"]
# Ausgabe des Maximalwerts und des Zeitpunkts
print(f"Maximalwert Parcour 2: {max_Parcour2} m/s² bei {max_time_Parcour2} s")

# Visualisierung Maximalwerte (1+2)
# Bestimmung Maximalwerte aller 3 Parcours und Darstellung als Balkendiagramm mit einfachem Code
max_values = {"Parcour 1": max_Parcour1, "Parcour 2": max_Parcour2}
plt.figure(figsize=(8, 5))
plt.bar(max_values.keys(), max_values.values(), color=["blue", "red"])
plt.ylabel("Maximalwert (m/s²)")

# Darstellung Zeitintervall1
t_1 = 1  # Beginn Zeitabschnitt in Sekunden
t_2 = 6  # Ende Zeitabschnitt in Sekunden
Parcour1_Zeitabschnitt1 = Parcour1[
    (Parcour1["Zeit"] >= t_1) & (Parcour1["Zeit"] <= t_2)
]
Parcour2_Zeitabschnitt1 = Parcour2[
    (Parcour2["Zeit"] >= t_1) & (Parcour2["Zeit"] <= t_2)
]

plt.figure(figsize=(12, 6))
plt.plot(
    Parcour1_Zeitabschnitt1["Zeit"],
    Parcour1_Zeitabschnitt1["Summe"],
    label="Parcour 1 (0-10s)",
    color="blue",
)
plt.plot(
    Parcour2_Zeitabschnitt1["Zeit"],
    Parcour2_Zeitabschnitt1["Summe"],
    label="Parcour 2 (0-10s)",
    color="red",
)
plt.xlabel("Zeit (s)")
plt.ylabel("Summe Beschleunigung (m/s²)")
plt.title(f"Vergleich der Parcours im Zeitabschnitt {t_1}-{t_2} Sekunden")
plt.legend()
plt.grid()



