---
title: 'Comment : créer un nouveau paramètre au moment du design'
description: Découvrez comment créer un paramètre de Windows Forms au moment de la conception à l’aide du concepteur de paramètres dans Visual Studio.
ms.date: 03/30/2017
helpviewer_keywords:
- application settings [Windows Forms], design time
- application settings [Windows Forms], creating
ms.assetid: c5d60a66-6507-462f-a81f-e3bc0a804e16
ms.openlocfilehash: ce37b42191999e29de2f2f7f7e7abfa0ec3f4d47
ms.sourcegitcommit: dc2feef0794cf41dbac1451a13b8183258566c0e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/24/2020
ms.locfileid: "85325845"
---
# <a name="how-to-create-a-new-setting-at-design-time"></a>Comment : créer un nouveau paramètre au moment du design

Vous pouvez créer un nouveau paramètre au moment du design à l’aide du concepteur de paramètres dans Visual Studio. Le concepteur de paramètres est une interface de style grille qui vous permet de créer de nouveaux paramètres et de spécifier des propriétés pour ces paramètres. Vous devez spécifier le nom, la valeur, le type et l’étendue de vos nouveaux paramètres. Une fois qu’un paramètre est créé, il est accessible dans le code.

## <a name="create-a-new-setting-at-design-time-in-c"></a>Créer un nouveau paramètre au moment du design en C\#

1. Ouvrez Visual Studio.

2. Dans **Explorateur de solutions**, développez le nœud **Propriétés** de votre projet.

3. Double-cliquez sur le fichier. Settings dans lequel vous souhaitez ajouter un nouveau paramètre. Le nom par défaut de ce fichier est Settings. Settings.

4. Dans le concepteur de paramètres, définissez le **nom**, la **valeur**, le **type**et la **portée** de votre paramètre. Chaque ligne représente un paramètre unique.

## <a name="create-a-new-setting-at-design-time-in-visual-basic"></a>Créer un nouveau paramètre au moment du design dans Visual Basic

1. Ouvrez Visual Studio.

2. Dans **Explorateur de solutions**, cliquez avec le bouton droit sur le nœud de votre projet et choisissez **Propriétés**.

3. Dans la page **Propriétés** , sélectionnez l’onglet **paramètres** .

4. Dans le concepteur de paramètres, définissez le **nom**, la **valeur**, le **type**et la **portée** de votre paramètre. Chaque ligne représente un paramètre unique.

## <a name="see-also"></a>Voir aussi

- [Utilisation de paramètres d'application et de paramètres utilisateur](using-application-settings-and-user-settings.md)
- [Vue d’ensemble des paramètres d’application](application-settings-overview.md)
- [Comment : modifier la valeur d'un paramètre existant au moment du design](how-to-change-the-value-of-an-existing-setting-at-design-time.md)
