---
title: 'Procédure : ajouter des références aux bibliothèques de types'
description: Découvrez comment ajouter des références aux bibliothèques de types dans Visual Studio ou pour la compilation à partir de la ligne de commande.
ms.date: 03/30/2017
helpviewer_keywords:
- importing type library
- interop assemblies, generating
- type libraries
- COM interop, importing type library
ms.assetid: f5cfa6ba-cc25-4017-82cd-ba7391859113
ms.openlocfilehash: 76f616c36d81b8245f77f011b5c2f9b945e6916b
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96255102"
---
# <a name="how-to-add-references-to-type-libraries"></a>Procédure : ajouter des références aux bibliothèques de types

Quand vous ajoutez une référence à une bibliothèque de types, Visual Studio génère un assembly d'interopérabilité contenant des métadonnées. Si un assembly PIA (Primary Interop Assembly) est disponible, Visual Studio utilise l'assembly existant avant de générer un nouvel assembly d'interopérabilité.  
  
### <a name="to-add-a-reference-to-a-type-library-in-visual-studio"></a>Pour ajouter une référence dans une bibliothèque de types Visual Studio  
  
1. Installez le fichier COM DLL ou EXE sur votre ordinateur, à moins que le fichier Setup.exe de Windows n'exécute l'installation à votre place.  
  
2. Choisissez **Projet**, **Ajouter une référence**.  
  
3. Dans le Gestionnaire de références, choisissez **COM**.  
  
4. Sélectionnez la bibliothèque de types dans la liste, ou naviguez jusqu'au fichier .tlb.  
  
5. Choisissez **OK**.  
  
6. Dans l’Explorateur de solutions, ouvrez le menu contextuel pour afficher la référence que vous venez d’ajouter, puis choisissez **Propriétés**.  
  
7. Dans la fenêtre **Propriétés**, vérifiez que la propriété **Incorporer les types interop** a la valeur **True**. Visual Studio incorpore alors les informations de type pour les types COM dans vos fichiers exécutables, en éliminant le besoin de déployer des assemblys PIA (Primary Interop Assembly) avec votre application.  
  
> [!NOTE]
> Les options de menu et de boîte de dialogue peuvent varier en fonction de la version de Visual Studio utilisée.  
  
### <a name="to-add-a-reference-to-a-type-library-for-command-line-compilation"></a>Pour ajouter une référence à une bibliothèque de types pour la compilation en ligne de commande  
  
1. Générez un assembly d’interopérabilité comme décrit dans [Guide pratique pour générer des assemblys d’interopérabilité à partir de bibliothèques de types](how-to-generate-interop-assemblies-from-type-libraries.md).  
  
2. Utilisez l’option [de compilateur-Link (options du compilateur C#)](../../csharp/language-reference/compiler-options/link-compiler-option.md) ou [-Link (Visual Basic)](../../visual-basic/reference/command-line-compiler/link.md) avec le nom de l’assembly d’interopérabilité pour incorporer les informations de type pour les types com dans vos fichiers exécutables.  
  
## <a name="see-also"></a>Voir aussi

- [Importation d'une bibliothèque de types sous la forme d'un assembly](importing-a-type-library-as-an-assembly.md)
- [Exposition de composants COM au .NET Framework](exposing-com-components.md)
- [Procédure pas à pas : incorporation de types provenant d’assemblys managés dans Visual Studio](../../standard/assembly/embed-types-visual-studio.md)
- [-link (Options du compilateur C#)](../../csharp/language-reference/compiler-options/link-compiler-option.md)
- [-Link (Visual Basic)](../../visual-basic/reference/command-line-compiler/link.md)
