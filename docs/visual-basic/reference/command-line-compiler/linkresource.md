---
title: -linkresource (Visual Basic)
ms.date: 03/10/2018
helpviewer_keywords:
- /linkresource compiler option [Visual Basic]
- -linkresource compiler option [Visual Basic]
- linkresource compiler option [Visual Basic]
- /linkres compiler option [Visual Basic]
- linkres compiler option [Visual Basic]
- -linkres compiler option [Visual Basic]
ms.assetid: cf4dcad8-17b7-404c-9184-29358aa05b15
ms.openlocfilehash: dee5384696d543442f3280b9fdb535a7d9b6f863
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/07/2019
ms.locfileid: "72005488"
---
# <a name="-linkresource-visual-basic"></a>-linkresource (Visual Basic)
Crée un lien à une ressource managée.  
  
## <a name="syntax"></a>Syntaxe  
  
```console  
-linkresource:filename[,identifier[,public|private]]  
```

ou  

```console
-linkres:filename[,identifier[,public|private]]  
```  
  
## <a name="arguments"></a>Arguments  
 `filename`  
 Obligatoire. Fichier de ressources à lier à l’assembly. Si le nom de fichier contient un espace, mettez-le entre guillemets ("").  
  
 `identifier`  
 facultatif. Nom logique de la ressource. Nom utilisé pour charger la ressource. La valeur par défaut est le nom du fichier. Si vous le souhaitez, vous pouvez spécifier si le fichier est public ou privé dans le manifeste de l’assembly, par exemple : `-linkres:filename.res,myname.res,public`. Par défaut, `filename` est public dans l’assembly.  
  
## <a name="remarks"></a>Notes  
 L’option `-linkresource` n’incorpore pas le fichier de ressources dans le fichier de sortie ; pour ce faire, utilisez l’option `-resource`.  
  
 L’option `-linkresource` requiert l’une des options `-target` autres que `-target:module`.  
  
 Si `filename` est un fichier de ressources .NET Framework créé, par exemple, par [Resgen. exe (générateur de fichiers de ressources)](../../../framework/tools/resgen-exe-resource-file-generator.md) ou dans l’environnement de développement, il est accessible avec les membres de l’espace de noms <xref:System.Resources>. (Pour plus d'informations, consultez <xref:System.Resources.ResourceManager>.) Pour accéder à toutes les autres ressources au moment de l’exécution, utilisez les méthodes qui commencent par `GetManifestResource` dans la classe <xref:System.Reflection.Assembly>.  
  
 Le nom de fichier peut être n’importe quel format de fichier. C’est le cas, par exemple, si vous voulez qu’une DLL native fasse partie de l'assembly pour qu’elle puisse être installée dans le Global Assembly Cache et accessible à partir du code managé dans l'assembly.  
  
 La forme abrégée de `-linkresource` est `-linkres`.  
  
> [!NOTE]
> L’option `-linkresource` n’est pas disponible à partir de l’environnement de développement Visual Studio. elle est disponible uniquement lorsque vous compilez à partir de la ligne de commande.  
  
## <a name="example"></a>Exemple  
 Le code suivant compile `in.vb` et les liens vers le fichier de ressources `rf.resource`.  
  
```console  
vbc -linkresource:rf.resource in.vb  
```  
  
## <a name="see-also"></a>Voir aussi

- [Compilateur de ligne de commande de Visual Basic](../../../visual-basic/reference/command-line-compiler/index.md)
- [-cible (Visual Basic)](../../../visual-basic/reference/command-line-compiler/target.md)
- [-ressource (Visual Basic)](../../../visual-basic/reference/command-line-compiler/resource.md)
- [Exemples de lignes de commande de compilation](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
