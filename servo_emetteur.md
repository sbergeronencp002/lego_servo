# Circuits électriques et servomoteur

# Tutoriel - Émetteur

## @showdialog

🎯 Objectif du programme
Transformer le micro:bit en émetteur radio qui envoie des commandes :

Bouton A → "Ouvrir"
Bouton B → "Fermer"

Ces messages seront reçus par un deuxième micro:bit relié à un servomoteur.

## Étape 1

Supprime le bloc ``||basic:toujours||`` (il n'est pas nécessaire).

## Étape 2

Ajout le bloc ``||radio:radio définir groupe||`` dans le bloc ``||basic:au démarrage||``.

```blocks

radio.setGroup(1)

```

## Étape 3

Modifie le bloc ``||radio:radio définir groupe||``.

Remplace la valeur ``||radio:1||`` par une valeur entre  ``||radio:1||`` et  ``||radio:255||``.

```blocks

radio.setGroup(1)

```
## @showdialog 

📡 Le groupe radio agit comme une fréquence privée.

✅ L'émetteur et le récepteur doivent avoir le même numéro (entre 1 et 255).

## Étape 4

Ajoute le bloc ``||radio:envoyer la chaîne par radio||`` dans le bloc ``||input:lorsque le bouton A est pressé||``.

```blocks

input.onButtonPressed(Button.A, function () {
    radio.sendString("")
})

```

## Étape 5

Modifie le bloc ``||radio:envoyer la chaîne par radio||``.

Ajoute le texte ``||text:Ouvrir||`` dans le bloc ``||radio:envoyer la chaîne par radio||``.

```blocks

input.onButtonPressed(Button.A, function () {
    radio.sendString("Ouvrir")
})

```

## Étape 6

Ajoute le bloc ``||radio:envoyer la chaîne par radio||`` dans le bloc ``||input:lorsque le bouton B est pressé||``.

```blocks

input.onButtonPressed(Button.B, function () {
    radio.sendString("")
})

```

## Étape 7

Modifie le bloc ``||radio:envoyer la chaîne par radio||``.

Ajoute le texte ``||text:Fermer||`` dans le bloc ``||radio:envoyer la chaîne par radio||``.

```blocks

input.onButtonPressed(Button.B, function () {
    radio.sendString("Fermer")
})

```

## @showdialog 

🧪 Test final.

Télécharge le programme sur le micro:bit émetteur.

Vérifie que le micro:bit récepteur utilise le même groupe radio.

Appuie sur A et B → observe le servomoteur