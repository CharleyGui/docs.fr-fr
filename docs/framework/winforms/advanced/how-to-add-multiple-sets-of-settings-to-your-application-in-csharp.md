---
title: 'Procédure : ajouter plusieurs jeux de paramètres à votre application en C#'
ms.date: 03/30/2017
helpviewer_keywords:
- application settings [Windows Forms], multiple sets
- application settings [Windows Forms], C#
ms.assetid: 45007ac6-cf07-4be7-bc38-3f0ef962faf9
ms.openlocfilehash: c6842d11c04e905d42734af939f2c3f0cfeacd47
ms.sourcegitcommit: cf9515122fce716bcfb6618ba366e39b5a2eb81e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/15/2019
ms.locfileid: "69040127"
---
# <a name="how-to-add-multiple-sets-of-settings-to-your-application-in-c"></a>Procédure : Ajouter plusieurs jeux de paramètres à votre application en C\#

Dans certains cas, vous souhaiterez peut-être avoir plusieurs jeux de paramètres dans une application. Par exemple, si vous développez une application dans laquelle un groupe de paramètres particulier est censé changer fréquemment, il peut être judicieux de les séparer en un seul fichier afin que le fichier puisse être remplacé en gros, laissant les autres paramètres non affectés. Visual Studio vous permet d’ajouter plusieurs jeux de paramètres à votre projet. Des ensembles de paramètres supplémentaires sont accessibles via l' `Properties.Settings` objet.

## <a name="add-an-additional-set-of-settings"></a>Ajouter un ensemble supplémentaire de paramètres

1. Dans Visual Studio, dans le menu **projet** , choisissez **Ajouter un nouvel élément**.

   La boîte de dialogue **Ajouter un nouvel élément** s’ouvre.

2. Dans la boîte de dialogue **Ajouter un nouvel élément** , sélectionnez **fichier de paramètres**, entrez un nom pour le fichier, puis cliquez sur **Ajouter** pour ajouter un nouveau fichier de paramètres à votre solution.

3. Dans **Explorateur de solutions**, faites glisser le nouveau fichier de paramètres dans le dossier **Propriétés** . Cela permet à vos nouveaux paramètres d’être disponibles dans le code.

4. Ajoutez et utilisez les paramètres de ce fichier comme vous le feriez pour tout autre fichier de paramètres. Vous pouvez accéder à ce groupe de paramètres via `Properties.Settings` l’objet.

## <a name="see-also"></a>Voir aussi

- [Utilisation de paramètres d'application et de paramètres utilisateur](using-application-settings-and-user-settings.md)
- [Vue d'ensemble des paramètres d'application](application-settings-overview.md)
