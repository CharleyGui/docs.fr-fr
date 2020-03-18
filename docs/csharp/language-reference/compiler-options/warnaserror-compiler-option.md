---
title: -warnaserror (Options du compilateur C#)
ms.date: 07/20/2015
f1_keywords:
- /warnaserror
helpviewer_keywords:
- /warnaserror compiler option [C#]
- -warnaserror compiler option [C#]
- warnaserror compiler option [C#]
ms.assetid: 04680ec3-08d6-4e2e-a274-38310e10e33c
ms.openlocfilehash: 7d43941629e933ac5a9e9c9d6a1388b6194f8d99
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "77503473"
---
# <a name="-warnaserror-c-compiler-options"></a>-warnaserror (Options du compilateur C#)
L’option **-warnaserror+** considère tous les avertissements comme des erreurs.  
  
## <a name="syntax"></a>Syntaxe  
  
```console  
-warnaserror[+ | -][:warning-list]  
```  
  
## <a name="remarks"></a>Notes   
 Les messages qui d’ordinaire auraient été signalés comme des avertissements s’affichent en tant qu’erreurs, et le processus de génération est arrêté (aucun fichier de sortie n’est généré).  
  
 Comme **-warnaserror** est activé par défaut, les avertissements n’empêchent pas la génération d’un fichier de sortie. Du fait de **-warnaserror**, qui est identique à **-warnaserror+**, les avertissements sont considérés comme des erreurs.  
  
 Le cas échéant, si vous voulez que seuls certains avertissements spécifiques soient considérés comme des erreurs, vous pouvez spécifier une liste séparée par des virgules qui liste les numéros d’avertissement à considérer comme des erreurs. L’ensemble de tous les avertissements d’annulation peut être spécifié avec le raccourci **annulé.**
  
 Utilisez [-warn](./warn-compiler-option.md) pour spécifier le niveau des avertissements que le compilateur doit afficher. Utilisez [-nowarn](./nowarn-compiler-option.md) pour désactiver certains avertissements.  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Pour définir cette option du compilateur dans l'environnement de développement Visual Studio  
  
1. Ouvrez la page **Propriétés** du projet.  
  
2. Cliquez sur la page de propriétés **Générer**.  
  
3. Modifiez la propriété **Considérer les avertissements comme des erreurs**.  
  
 Pour définir cette option du compilateur par programmation, consultez <xref:VSLangProj80.CSharpProjectConfigurationProperties3.TreatWarningsAsErrors>.  
  
## <a name="example"></a> Exemple  
 Compilez `in.cs` et faites en sorte que le compilateur n’affiche aucun avertissement :  
  
```console  
csc -warnaserror in.cs  
csc -warnaserror:642,649,652,nullable in.cs  
```  
  
## <a name="see-also"></a>Voir aussi

- [Options de compilateur C](./index.md)
- [Gestion des propriétés des projets et des solutions](/visualstudio/ide/managing-project-and-solution-properties)
