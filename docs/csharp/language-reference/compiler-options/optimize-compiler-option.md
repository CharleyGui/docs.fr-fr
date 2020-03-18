---
title: -optimize (Options du compilateur C#)
ms.date: 07/20/2015
f1_keywords:
- /optimize
helpviewer_keywords:
- /optimize compiler option [C#]
- -o compiler option [C#]
- optimize compiler option [C#]
- /o compiler option [C#]
- -optimize compiler option [C#]
- compiler optimization [C#]
- o compiler option [C#]
ms.assetid: 6dd5b6f2-cd1d-4593-a9f4-1c2ed9404ca0
ms.openlocfilehash: bec99ca582070a99fd8b734ef8a7b9e71d945488
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "69606602"
---
# <a name="-optimize-c-compiler-options"></a>-optimize (Options du compilateur C#)
L’option **-optimize** active ou désactive les optimisations effectuées par le compilateur pour réduire la taille de votre fichier de sortie et le rendre plus rapide et plus efficace.  
  
## <a name="syntax"></a>Syntaxe  
  
```console  
-optimize[+ | -]  
```  
  
## <a name="remarks"></a>Notes   
 **-optimize** indique aussi au Common Language Runtime d’optimiser le code au moment de l’exécution.  
  
 Par défaut, les optimisations sont désactivées. Pour activer les optimisations, spécifiez **-optimize+**.  
  
 Quand vous créez un module destiné à être utilisé par un assembly, utilisez les mêmes paramètres **-optimize** que ceux de l’assembly.  
  
 **-o** est la forme abrégée de **-optimize**.  
  
 Il est possible de combiner les options **-optimize** et [-debug](./debug-compiler-option.md).  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Pour définir cette option du compilateur dans l'environnement de développement Visual Studio  
  
1. Ouvrez la page **Propriétés** du projet.  
  
2. Cliquez sur la page de propriétés **Générer**.  
  
3. Modifiez la propriété **Optimiser le code**.  
  
 Pour plus d’informations sur la façon de définir cette option du compilateur par programmation, consultez <xref:VSLangProj80.CSharpProjectConfigurationProperties3.Optimize%2A>.  
  
## <a name="example"></a> Exemple  
 Compilez `t2.cs` et activez les optimisations du compilateur :  
  
```console  
csc t2.cs -optimize  
```  
  
## <a name="see-also"></a>Voir aussi

- [Options de compilateur C](./index.md)
- [Gestion des propriétés des projets et des solutions](/visualstudio/ide/managing-project-and-solution-properties)
