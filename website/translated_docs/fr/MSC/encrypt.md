---
id: encrypt
title: Page chiffrement
sidebar_label: Page chiffrement
---

Vous pouvez vous aider de cette page pour chiffrer ou *déchiffrer* (i.e. enlever le chiffrement) le fichier de données, en fonction du statut de l'attribut **Chiffrable** défini pour chaque table de la base. For detailed information about data encryption in 4D, please refer to the "Encrypting data" section in the *Design Reference* manual.

Un nouveau dossier est créé à chaque opération de chiffrement/déchiffrement. Il est nommé "Replaced Files (Encrypting) *yyyy-mm-dd hh-mm-ss*" ou "Replaced Files (Decrypting) *yyyy-mm-dd hh-mm-ss*".
> Le chiffrement est disponible uniquement en [mode maintenance](overview.md#display-in-maintenance-mode). Si vous tentez d’effectuer cette opération en mode standard, une boîte de dialogue d’alerte vous prévient que l'application va être fermée puis relancée en mode maintenance

**Attention :**
- Le chiffrement d'un fichier de données est une opération de longue durée. Un indicateur de progression de l'opération s'affiche (et peut être interrompu par l'utilisateur). À noter également que le chiffrement d'une application comprend toujours une étape de compactage.
- Chaque opération de chiffrement génère une copie du fichier de données, ce qui augmente la taille du dossier de l'application. Il est important de prendre cela en considération (notamment sous macOS, où les applications 4D apparaissent sous forme de paquet) afin de ne pas augmenter excessivement la taille de l'application. Le déplacement ou la suppression manuels des copies du fichier original dans le paquet peut aider à réduire la taille du paquet.

## Chiffrer des données pour la première fois
Trois étapes sont nécessaires pour effectuer le tout premier chiffrement de vos données à l'aide du CSM :

1. Dans l'éditeur de structure, cochez l'attribut **Chiffrable** pour chaque table dont vous souhaitez chiffrer les données. Consultez la section "Propriétés des tables".
2. Ouvrez la page Chiffrement du CSM. If you open the page without setting any tables as **Encryptable**, the following message is displayed in the page: ![](assets/en/MSC/MSC_encrypt1.png) Otherwise, the following message is displayed: ![](assets/en/MSC/MSC_encrypt2.png)<p> This means that the **Encryptable** status for at least one table has been modified and the data file still has not been encrypted. **Note : **Le même message s'affiche lorsque le statut **Chiffrable** a été modifié dans un fichier de données déjà chiffré ou après le déchiffrement d'un fichier de données (voir ci-dessous).
3. Cliquez sur le bouton de Chiffrement.  
   ![](assets/en/MSC/MSC_encrypt3.png)  
   Vous serez ensuite invité à saisir une phrase secrète pour votre fichier de données : ![](assets/fr/MSC/MSC_encrypt4.png) La phrase secrète est utilisée pour générer la clé de chiffrement des données. Une phrase secrète est une version plus sécurisée d'un mot de passe et peut contenir un grand nombre de caractères. For example, you could enter a passphrases such as "We all came out to Montreux" or "My 1st Great Passphrase!!" The security level indicator can help you evaluate the strength of your passphrase: ![](assets/en/MSC/MSC_encrypt5.png) (deep green is the highest level)
4. Tapez sur Entrée pour confirmer votre phrase secrète sécurisée.

Le processus de chiffrement est alors lancé. If the MSC was opened in standard mode, the application is reopened in maintenance mode.

4D propose de sauvegarder la clé de chiffrement (voir le paragraphe [Sauvegarder la clé de chiffrement](#saving-the-encryption-key) ci-dessous). Vous pouvez la sauvegarder à ce moment précis ou bien ultérieurement. Vous pouvez également ouvrir le fichier d'historique du chiffrement.

Si le processus de chiffrement est réussi, la page Chiffrement affiche les boutons Opérations de maintenance liées au chiffrement.

**Attention :** Durant l'opération de chiffrement, 4D créé un nouveau fichier de données vide et y insère des données à partir du fichier de données original. Les enregistrements correspondant aux tables "chiffrées" sont chiffrés puis copiés ; les autres enregistrements sont uniquement copiés (une opération de compactage est également exécutée). Si l'opération est réussie, le fichier de données original est déplacé vers un dossier "Replaced Files (Encrypting)". If you intend to deliver an encrypted data file, make sure to move/remove any unencrypted data file from the application folder beforehand.

## Opérations de maintenance liées au chiffrement
When an application is encrypted (see above), the Encrypt page provides several encryption maintenance operations, corresponding to standard scenarios. ![](assets/fr/MSC/MSC_encrypt6.png)


### Fournir la clé de chiffrement des données actuelle
Pour des raisons de sécurité, toutes les opérations de maintenance liées au chiffrement nécessitent la clé de chiffrement des données actuelle.

- Si la clé de chiffrement des données est déjà chargée dans le trousseau 4D(1), elle est automatiquement réutilisée par 4D.
- Si la clé de chiffrement des données n'est pas identifiée, vous devez la fournir. La boîte de dialogue suivante s'affiche : ![](assets/fr/MSC/MSC_encrypt7.png)

À ce stade, deux options s'offrent à vous :
- entrer la phrase secrète actuelle(2) et cliquer sur **OK**. OU
- connecter un appareil tel qu'une clé USB et cliquer sur le bouton **Scanner les disques**.

(1) Le trousseau de 4D stocke toutes les clés de chiffrement de données valides saisies durant la session d'application session.   
(2) Le mot de passe actuel correspond au mot de passe utilisé pour générer la clé de chiffrement actuelle.

Dans tous les cas, si des informations valides sont fournies, 4D redémarre en mode maintenance (si ce n'est pas déjà le cas) et exécute l'opération.

### Re-chiffrer les données à l'aide de la clé de chiffrement actuelle

Cette opération est utile lorsque l'attribut **Chiffrable** a été modifié pour une ou plusieurs tables contenant des données. Dans ce cas, afin d'éviter toute incohérence dans le fichier de données, 4D désactive l'accès en écriture aux enregistrements des tables dans l'application. Il est alors nécessaire de re-chiffrer les données pour restituer un statut de chiffrement valide.

1. Cliquez sur **Re-chiffrer les données à l'aide de la clé actuelle**.
2. Saisissez la clé de chiffrement des données actuelle.

Le fichier de données est correctement re-chiffré à l'aide de la clé actuelle et un message de confirmation s'affiche : ![](assets/fr/MSC/MSC_encrypt8.png)

### Changer votre phrase secrète et re-chiffrer les données
Cette opération est utile en cas de modification de la clé de chiffrement des données actuelle. Par exemple, il se peut que vous la modifiiez pour vous conformer aux règles de sécurité (telles que la nécessité de modifier la phrase secrète tous les trois mois).

1. Cliquez sur **Changer votre phrase secrète et re-chiffrer les données**.
2. Saisissez la clé de chiffrement des données actuelle.
3. Saisissez la nouvelle phrase secrète (pour plus de sécurité, il vous est demandé de la saisir deux fois) : ![](assets/en/MSC/MSC_encrypt9.png) Le fichier de données est entièrement déchiffré et un message de confirmation s'affiche : ![](assets/fr/MSC/MSC_encrypt8.png)

### Enlever le chiffrement de toutes les données
Cette opération supprime tout le chiffrement du fichier de données. Si vous ne souhaitez plus que vos données soient chiffrées :

1. Cliquez sur **Enlever le chiffrement de toutes les données**.
2. Saisissez la clé de chiffrement de données actuelle (voir Fournir la clé de chiffrement des données actuelle).

Le fichier de données est entièrement déchiffré et un message de confirmation s'affiche : ![](assets/en/MSC/MSC_encrypt10.png)
> Une fois que le fichier de données est déchiffré, le statut de chiffrement des tables ne correspond plus à leur attribut Chiffrable. Pour restituer un statut de mise en correspondance, vous devez décocher tous les attributs **Chiffrable** au niveau de la structure de la base.

## Sauvegarder la clé de chiffrement

4D vous permet de sauvegarder la clé de chiffrement des données dans un fichier créé à cet effet. Storing this file on an external device such a USB key will facilitate the use of an encrypted application, since the user would only need to connect the device to provide the key before opening the application in order to access encrypted data.

Vous pouvez sauvegarder la clé de chiffrement chaque fois qu'une nouvelle phrase secrète est fournie :

- when the application is encrypted for the first time,
- when the application is re-encrypted with a new passphrase.

Les clés de chiffrement successives peuvent être sauvegardées sur le même appareil.

## Fichier d'historique
After an encryption operation has been completed, 4D generates a file in the Logs folder of the application. It is created in XML format and named "*ApplicationName_Encrypt_Log_yyyy-mm-dd hh-mm-ss.xml*" or "*ApplicationName_Decrypt_Log_yyyy-mm-dd hh-mm-ss.xml*".

Chaque fois qu'un nouveau fichier d'historique est généré, un bouton Voir le compte rendu s'affiche dans la page CSM.

Le fichier d'historique liste toutes les opérations internes liées au processus de chiffrement/déchiffrement qui ont été exécutées, ainsi que les erreurs (le cas échéant).
