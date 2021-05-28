## Known variables

- "Axe sous puissance" (%I0.1): is the conveyor's motor powered/started?
- "Presence pot" (%I0.3): is there a container on the conveyor, below the silo?
- "Presence Produit" (%I0.5): is the silo not empty?
- "Accumulation Aval B5" (%I0.6): has a container reached the end of the conveyor?
- "Axe_Remplissage_Sens" (%Q0.1): is the silo's motor going forward/backward?
- "Mise sous puissance" (%Q0.2): is the silo's motor starting?
- "Electro Aimant" (%Q0.5): is the silo's magnetic valve closed?
- "Verine Verte" (%Q0.4): is the stacklight's green color lit?
- "BP_Initialisation" (%M5.2): is the init push button pressed?
- "BP Marche" (%M5.0): is the on push button pressed?
- "BP Arrêt" (%M5.4): is the off push button pressed?
- "BP Manu" (%M5.3): is the push button to switch to manual mode pressed?
- "BP Manu+" (%M4.6): is the push button to manually move the silo forward pressed?
- "BP Manu-" (%M4.7): is the push button to manual move the silo backward pressed?
- "Temps Remplissage (%MD100): elapsed time between opening and closing of magnetic valve
- "Axe_Remplissage_Position_int" (%MW220): position of the silo on X axis
- "Glissement V20" (%MD60): conveyor speed
- "Accélération V90" (%MD64): silo's acceleration on X axis
- "Pause" (%M310.2): emergency stop
- "N d'Arret" (%MW254): number of incidents on machine (idle time)
- "Duree_Arrets_Cumules" (%MW256): cumulated idling time
- "Compteur pots" (%MW250): number of containers having reached the end of the conveyor
- "Compteur_Horaire" (%MD258): up time in second

(difference between %I0.1 and %Q0.2)

## Control rules

- **if** %I0.3 and %I0.5 are _true_, **then** set %Q0.5 to _false_ and %Q0.2 to _true_
- after %MD100 in seconds, set %Q0.1 to _false_
- **if** [motor reached end of axis?], **then** set %Q0.2 to _false_
- **if** %I0.6 is _true_, **then** increment %MW250