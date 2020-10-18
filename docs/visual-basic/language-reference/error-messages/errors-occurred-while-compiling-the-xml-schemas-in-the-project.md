---
title: Des erreurs se sont produites lors de la compilation des schémas Xml du projet
ms.date: 07/20/2015
f1_keywords:
- bc36810
- vbc36810
helpviewer_keywords:
- BC36810
ms.assetid: 9323b5d2-ba14-4e49-91f1-9ad647162144
ms.openlocfilehash: 747c2c8cb1e5dc3d4fcae86a9acf84446c4e59c9
ms.sourcegitcommit: ff5a4eb5cffbcac9521bc44a907a118cd7e8638d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/17/2020
ms.locfileid: "92162035"
---
# <a name="bc36810-errors-occurred-while-compiling-the-xml-schemas-in-the-project"></a>BC36810 : des erreurs se sont produites lors de la compilation des schémas XML dans le projet

Des erreurs se sont produites lors de la compilation des schémas XML dans le projet. Pour cette raison, XML IntelliSense n’est pas disponible.

 Il y a une erreur dans un schéma XSD (XML Schema Definition) inclus dans le projet. Cette erreur se produit lorsque vous ajoutez un fichier de schéma XSD (. xsd) qui est en conflit avec le jeu de schémas XSD existant pour le projet.

 **ID d’erreur :** BC36810

## <a name="to-correct-this-error"></a>Pour corriger cette erreur

- Double-cliquez sur l’avertissement dans la fenêtre **liste d’erreurs** . Visual Basic vous reconnectera à l’emplacement dans le fichier XSD qui est la source de l’avertissement. Corrigez l’erreur dans le schéma XSD.

- Assurez-vous que tous les fichiers de schéma XSD (. xsd) requis sont inclus dans le projet. Vous devrez peut-être cliquer sur **Afficher tous les fichiers** dans le menu **projet** pour afficher vos fichiers. xsd dans **Explorateur de solutions**. Cliquez avec le bouton droit sur un fichier. xsd, puis cliquez sur **inclure dans le projet** pour inclure le fichier dans votre projet.

- Si vous utilisez l’Assistant XML vers schéma, cette erreur peut se produire si vous déduisez des schémas plus d’une fois à partir de la même source. Dans ce cas, vous pouvez supprimer les fichiers de schéma XSD existants du projet, ajouter un nouveau modèle d’élément de schéma XML à, puis fournir l’Assistant XML au schéma avec toutes les sources XML applicables à votre projet.

- Si aucune erreur n’est identifiée dans votre schéma XSD, le compilateur XML peut ne pas disposer d’informations suffisantes pour fournir un message d’erreur détaillé. Vous pourrez peut-être obtenir des informations d’erreur plus détaillées si vous vous assurez que les espaces de noms XML des fichiers. xsd inclus dans votre projet correspondent aux espaces de noms XML identifiés pour le jeu de schémas XML dans Visual Studio.

## <a name="see-also"></a>Voir aussi

- [Fenêtre Liste d’erreurs](/visualstudio/ide/reference/error-list-window)
- [XML](../../programming-guide/language-features/xml/index.md)
