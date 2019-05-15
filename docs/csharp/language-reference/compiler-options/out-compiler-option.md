---
title: -out (Options du compilateur C#)
ms.date: 07/20/2015
f1_keywords:
- /out
helpviewer_keywords:
- /out compiler option [C#]
- out compiler option [C#]
- -out compiler option [C#]
ms.assetid: 70d91d01-7bd2-4aea-ba8b-4e9807e9caa5
ms.openlocfilehash: 0cb0b78396731a9b8e127430cd06a9e71812d4fd
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64593034"
---
# <a name="-out-c-compiler-options"></a>-out (Options du compilateur C#)
L’option **-out** spécifie le nom du fichier de sortie.  
  
## <a name="syntax"></a>Syntaxe  
  
```console  
-out:filename  
```  
  
## <a name="arguments"></a>Arguments  
 `filename`  
 Nom du fichier de sortie créé par le compilateur.  
  
## <a name="remarks"></a>Remarques  
 Sur la ligne de commande, il est possible de spécifier plusieurs fichiers de sortie pour une même compilation. Le compilateur s’attend à trouver un ou plusieurs fichiers de code source à la suite de l’option **-out**. Ensuite, tous les fichiers de code source sont compilés dans le fichier de sortie spécifié par cette option **-out**.  
  
 Spécifiez le nom complet et l’extension du fichier que vous voulez créer.  
  
 Si vous ne spécifiez pas le nom du fichier de sortie :  
  
- Un fichier .exe prend le nom du fichier de code source qui contient la méthode **Main**.  
  
- Un fichier .dll ou .netmodule prend le nom du premier fichier de code source.  
  
 Un fichier de code source ayant servi à compiler un fichier de sortie ne peut pas être utilisé dans une même compilation pour compiler un autre fichier de sortie.  
  
 Au moment de générer plusieurs fichiers de sortie lors d’une compilation en ligne de commande, gardez à l’esprit que seul un fichier de sortie peut faire office d’assembly et que seul le premier fichier de sortie spécifié (implicitement ou explicitement avec **-out**) peut être l’assembly.  
  
 Les modules générés dans le cadre d’une compilation deviennent des fichiers associés à un assembly également généré pendant la compilation. Utilisez [ildasm.exe](../../../framework/tools/ildasm-exe-il-disassembler.md) pour afficher le manifeste d’assembly et identifier les fichiers associés.  
  
 L’option de compilateur -out est nécessaire pour faire d’un fichier exe la cible d’un assembly friend. Pour plus d’informations, consultez [Assemblys friend](../../../standard/assembly/friend-assemblies.md).  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Pour définir cette option du compilateur dans l'environnement de développement Visual Studio  
  
1. Ouvrez la page **Propriétés** du projet.  
  
2. Cliquez sur la page de propriétés **Application**.  
  
3. Modifiez la propriété **Nom de l’assembly**.  
  
     Pour définir cette option de compilateur par programmation : <xref:VSLangProj80.ProjectProperties3.OutputFileName%2A> est une propriété en lecture seule, qui est déterminée par une combinaison du type de projet (exe, bibliothèque, etc.) et le nom de l’assembly. Il est nécessaire de modifier l’une de ces propriétés (ou les deux) pour définir le nom du fichier de sortie.  
  
## <a name="example"></a>Exemple  
 Compilez `t.cs` et créez le fichier de sortie `t.exe`, puis générez `t2.cs` et créez le fichier de sortie de module `mymodule.netmodule` :  
  
```console  
csc t.cs -out:mymodule.netmodule -target:module t2.cs  
```  
  
## <a name="see-also"></a>Voir aussi

- [Options du compilateur C#](../../../csharp/language-reference/compiler-options/index.md)
- [Assemblys friend](../../../standard/assembly/friend-assemblies.md)
- [Gestion des propriétés des projets et des solutions](/visualstudio/ide/managing-project-and-solution-properties)
