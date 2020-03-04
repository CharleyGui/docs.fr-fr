---
title: -checked (Options du compilateur C#)
ms.date: 07/20/2015
f1_keywords:
- /checked
helpviewer_keywords:
- checked compiler option [C#]
- -checked compiler option [C#]
- /checked compiler option [C#]
ms.assetid: fb7475d3-e6a6-4e6d-b86c-69e7a74c854b
ms.openlocfilehash: 44dc0fc8f50e5248ce2fca17c36f7309a6aca8d1
ms.sourcegitcommit: 43d10ef65f0f1fd6c3b515e363bde11a3fcd8d6d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/03/2020
ms.locfileid: "78239690"
---
# <a name="-checked-c-compiler-options"></a>-checked (Options du compilateur C#)
L’option **-checked** spécifie si une instruction arithmétique entière qui produit une valeur en dehors de la plage du type de données, et qui n’est pas dans la portée d’un mot clé [checked](../keywords/checked.md) ou [unchecked](../keywords/unchecked.md), doit provoquer une exception au moment de l’exécution.  
  
## <a name="syntax"></a>Syntaxe  
  
```console  
-checked[+ | -]  
```  
  
## <a name="remarks"></a>Notes  
 Une instruction arithmétique entière qui est dans la portée d’un mot clé `checked` ou `unchecked` n’est pas soumise à l’effet de l’option **-checked**.  
  
 Si une instruction arithmétique entière qui n’est pas dans la portée d’un mot clé `checked` ou `unchecked` produit une valeur en dehors de la plage du type de données, et que **-checked+** (ou **-checked**) est utilisé dans la compilation, cette instruction provoque une exception au moment de l’exécution. Si **-checked-** est utilisé dans la compilation, cette instruction ne provoque pas d’exception au moment de l’exécution.  
  
 La valeur par défaut de cette option est **-checked-**. La vérification du dépassement de capacité est désactivée.
 
 Certains outils automatisés qui sont utilisés pour générer des applications volumineuses définissent l’option -checked sur +. Un scénario d’usage de l’option -checked- est de substituer l’option globale par défaut de l’outil en spécifiant -checked-.
 
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Pour définir cette option du compilateur dans l’environnement de développement Visual Studio  
  
1. Ouvrez la page **Propriétés** du projet. Pour plus d’informations, consultez [Générer, page du Concepteur de projets (C#)](/visualstudio/ide/reference/build-page-project-designer-csharp).  
  
2. Cliquez sur la page de propriétés **Générer**.  
  
3. Cliquez sur le bouton **Avancé**.  
  
4. Modifiez la propriété **Vérifier la débordement arithmétique** .  
  
 Pour accéder à cette option du compilateur par programmation, consultez <xref:VSLangProj80.CSharpProjectConfigurationProperties3.CheckForOverflowUnderflow%2A>.  
  
## <a name="example"></a>Exemple  
 La commande suivante compile `t2.cs`. L’utilisation de `-checked` dans la commande spécifie que toute instruction arithmétique entière dans le fichier qui n’est pas dans la portée d’un mot clé `checked` ou `unchecked`, et qui produit une valeur en dehors de la plage du type de données, provoque une exception au moment de l’exécution.  
  
```console  
csc t2.cs -checked  
```  
  
## <a name="see-also"></a>Voir aussi

- [Options du compilateur C#](./index.md)
- [Gestion des propriétés des projets et des solutions](/visualstudio/ide/managing-project-and-solution-properties)
