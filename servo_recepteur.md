# Circuits électriques et servomoteur

# Tutoriel - Récepteur

## @showdialog

🎯 Objectif du programme

⚙️ Transformer le micro:bit en récepteur radio qui :

➡️ reçoit "Ouvrir" ou "Fermer"

➡️ contrôle un servomoteur sur la broche P16

➡️ affiche l'état avec DEL verte (ouvert) ou DEL rouge (fermé).

## Étape 1

Supprime le bloc ``||basic:toujours||``.

✅ Le programme fonctionne uniquement lors de la réception radio.

## Étape 2

Ajoute le bloc ``||radio:radio définir groupe||`` dans le bloc ``||basic:au démarrage||``.

```blocks

radio.setGroup(1)

```

## Étape 3

Modifie le bloc ``||radio:radio définir groupe||``.

Remplace la valeur ``||radio:1||`` par une valeur entre  ``||radio:1||`` et  ``||radio:255||``.

📡 Le numéro du groupe radio doit être IDENTIQUE sur l'émetteur et le récepteur.

```blocks

radio.setGroup(1)

```

## Étape 4

Ajoute le bloc ``|| pins: régler position servo ||`` sous le bloc ``||radio:radio définir groupe||``.

```blocks

radio.setGroup(1)
pins.servoWritePin(AnalogPin.P0, 180)
```

## Étape 5

Modifie les valeurs du bloc ``|| pins: régler position servo ||``.

Remplace la broche ``|| pins: P0 ||`` par ``|| pins: P16 ||``.

Remplace la valeur ``|| pins: 180 ||`` par ``|| pins: 0 ||``.

```blocks

radio.setGroup(1)
pins.servoWritePin(AnalogPin.P16, 0)

```

## Étape 6

Ajoute deux blocs ``|| pins: écrire sur la broche ||`` sous le bloc ``|| pins: régler position servo ||``.

P12 = Vert - P14 = Rouge

```blocks

radio.setGroup(1)
pins.servoWritePin(AnalogPin.P16, 0)
pins.digitalWritePin(DigitalPin.P0, 0)
pins.digitalWritePin(DigitalPin.P0, 0)

```

## Étape 7

Modifie les valeurs des blocs ``|| pins: écrire sur la broche ||``.

Remplace les broches ``|| pins: P0 ||`` par ``|| pins: P12 ||`` et ``|| pins: P14 ||``.

Les valeurs ``|| pins: 0 ||`` demeurent les mêmes.

P12 = Vert - P14 = Rouge

```blocks

radio.setGroup(1)
pins.servoWritePin(AnalogPin.P16, 0)
pins.digitalWritePin(DigitalPin.P12, 0)
pins.digitalWritePin(DigitalPin.P14, 0)

```

## Étape 8

Ajoute le bloc ``||logic:si vrai alors||`` dans le bloc ``||radio:quand une donnée est reçue par radio receivedString||``.

```blocks

radio.onReceivedString(function (receivedString) {
    if (true) {
        
    }
})

```

## Étape 9

Remplace la valeur ``||logic:vrai||`` du bloc ``||logic:si vrai alors||`` par le bloc ``||logic:"" = ""||``.

```blocks

radio.onReceivedString(function (receivedString) {
    if ("" == "") {
        
    }
})

```

## Étape 10

Modifie le bloc ``||logic:"" = ""||``.

Remplace ``||logic:""||`` de gauche par le bloc ``||pins:receivedString||``. 

Pour y arriver, fais glisser le bloc ``||pins:receivedString||`` du bloc ``||radio:quand une donnée est reçue par radio receivedString||`` dans le bloc ``||logic:""||`` de gauche.

```blocks

radio.onReceivedString(function (receivedString) {
    if (receivedString == "") {
        
    }
})

```

## Étape 11

Modifie le bloc ``||logic:"" = ""||``. 

Remplace ``||logic:""||`` de droite par le mot **Ouvrir**. 

```blocks

radio.onReceivedString(function (receivedString) {
    if (receivedString == "Ouvrir") {
        
    }
})

```

## Étape 12

Ajoute le bloc ``||logic:si vrai alors||`` sous le bloc ``||logic:si vrai alors||``.

```blocks

radio.onReceivedString(function (receivedString) {
    if (receivedString == "Ouvrir") {
        
    }
    if (true) {
        
    }
})

```

## Étape 13

Remplace la valeur ``||logic:vrai||`` du bloc ``||logic:si vrai alors||`` par le bloc ``||logic:"" = ""||``.

```blocks

radio.onReceivedString(function (receivedString) {
    if (receivedString == "Ouvrir") {
        
    }
    if ("" == "") {
        
    }
})

```

## Étape 14

Modifie le bloc ``||logic:"" = ""||``.

Remplace le bloc ``||logic:""||`` de gauche par le bloc ``||pins:receivedString||``. 

Pour y arriver, fais glisser le bloc ``||pins:receivedString||`` du bloc ``||radio:quand une donnée est reçue par radio receivedString||`` dans le bloc ``||logic:""||`` de gauche.

```blocks

radio.onReceivedString(function (receivedString) {
    if (receivedString == "Ouvrir") {
        
    }
    if (receivedString == "") {
        
    }
})

```

## Étape 15

Remplace le bloc ``||logic:""||`` de droite par le mot **Fermer**. 

```blocks

radio.onReceivedString(function (receivedString) {
    if (receivedString == "Ouvrir") {
        
    }
    if (receivedString == "Fermer") {
        
    }
})

```

## Étape 16

Modifie le bloc ``||logic:"Ouvrir"||``.

Regarde l'indice.

```blocks

radio.onReceivedString(function (receivedString) {
    if (receivedString == "Ouvrir") {
pins.servoWritePin(AnalogPin.P16, 90)
pins.digitalWritePin(DigitalPin.P12, 1)
pins.digitalWritePin(DigitalPin.P14, 0)
    }
    if (receivedString == "Fermer") {
    }
})

```

## Étape 17

Modifie le bloc ``||logic:"Fermer"||``.

Regarde l'indice.

```blocks


radio.onReceivedString(function (receivedString) {
    if (receivedString == "Ouvrir") {
        pins.servoWritePin(AnalogPin.P16, 90)
        pins.digitalWritePin(DigitalPin.P12, 1)
        pins.digitalWritePin(DigitalPin.P14, 0)
    }
    if (receivedString == "Fermer") {
        pins.servoWritePin(AnalogPin.P16, 0)
        pins.digitalWritePin(DigitalPin.P12, 0)
        pins.digitalWritePin(DigitalPin.P14, 1)
    }
})

```

## @showdialog 

🧪 Test final

Téléverse le programme sur le récepteur.
Branche le servo sur P16.

⚙️ Branche les DEL :

🟢 Vert → P12
🔴 Rouge → P14

👉 Appuie sur A et B de l'émetteur.

🎉 Le système est maintenant complet et fonctionnel !