---
title: -nowarn (options du compilateur C#)
ms.date: 07/20/2015
f1_keywords:
- /nowarn
helpviewer_keywords:
- nowarn compiler option [C#]
- /nowarn compiler option [C#]
- -nowarn compiler option [C#]
ms.assetid: 6dcbc5e8-ae67-4566-9df3-f63cfdd9c4e4
ms.openlocfilehash: b455a2f719e7350c51cf4a1f095d4669529d0e5e
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64592811"
---
# <a name="-nowarn-c-compiler-options"></a>-nowarn (options du compilateur C#)
L’option **-nowarn** vous permet de désactiver l’affichage d’un ou plusieurs avertissements par le compilateur. Séparez les numéros des avertissements par une virgule.  
  
## <a name="syntax"></a>Syntaxe  
  
```console  
-nowarn:number1[,number2,...]  
```  
  
## <a name="arguments"></a>Arguments  
 `number1`, `number2`  
 Numéro de chaque avertissement que le compilateur ne doit pas afficher.  
  
## <a name="remarks"></a>Remarques  
 Vous devez spécifier uniquement la partie numérique de l’identificateur d’avertissement. Par exemple, si vous souhaitez supprimer l’avertissement CS0028, spécifiez `-nowarn:28`.  
  
 Le compilateur ignore automatiquement les numéros des avertissements passés à `-nowarn` qui étaient valides dans les versions précédentes, mais qui ont été supprimés dans le compilateur. Par exemple, l’avertissement CS0679 était valide dans le compilateur dans Visual Studio .NET 2002, mais il a été supprimé depuis cette version.  
  
 Les avertissements suivants ne peuvent pas être supprimés avec l’option `-nowarn` :  
  
- Avertissement du compilateur (niveau 1) CS2002  
  
- Avertissement du compilateur (niveau 1) CS2023  
  
- Avertissement du compilateur (niveau 1) CS2029  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Pour définir cette option du compilateur dans l'environnement de développement Visual Studio  
  
1. Ouvrez la page **Propriétés** du projet. Pour plus de détails, consultez [Générer, page du Concepteur de projet (C#)](/visualstudio/ide/reference/build-page-project-designer-csharp).  
  
2. Cliquez sur la page de propriétés **Générer**.  
  
3. Modifiez la propriété **Supprimer les avertissements**.  
  
 Pour plus d'informations sur la façon de définir cette option du compilateur par programme, consultez <xref:VSLangProj80.ProjectProperties3.DelaySign%2A>.  
  
## <a name="see-also"></a>Voir aussi

- [Options du compilateur C#](../../../csharp/language-reference/compiler-options/index.md)
- [Gestion des propriétés des projets et des solutions](/visualstudio/ide/managing-project-and-solution-properties)
- [Erreurs du compilateur C#](../../../csharp/language-reference/compiler-messages/index.md)
