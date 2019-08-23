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
ms.openlocfilehash: d92b0d08daf660880b648875c67c3b78069143d3
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69924855"
---
# <a name="-linkresource-visual-basic"></a>-linkresource (Visual Basic)
Crée un lien à une ressource managée.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
-linkresource:filename[,identifier[,public|private]]  
' -or-  
-linkres:filename[,identifier[,public|private]]  
```  
  
## <a name="arguments"></a>Arguments  
 `filename`  
 Requis. Fichier de ressources à lier à l’assembly. Si le nom de fichier contient un espace, mettez-le entre guillemets ("").  
  
 `identifier`  
 facultatif. Nom logique de la ressource. Nom utilisé pour charger la ressource. La valeur par défaut est le nom du fichier. Si vous le souhaitez, vous pouvez spécifier si le fichier est public ou privé dans le manifeste de l’assembly, par exemple: `-linkres:filename.res,myname.res,public`. Par défaut, `filename` est public dans l’assembly.  
  
## <a name="remarks"></a>Notes  
 L' `-linkresource` option n’incorpore pas le fichier de ressources dans le fichier de sortie `-resource` ; utilisez l’option pour effectuer cette opération.  
  
 L' `-linkresource` option requiert l’une `-target` des options autres que `-target:module`.  
  
 Si `filename` est un fichier de ressources de .NET Framework créé, par exemple, par [Resgen. exe (générateur de fichiers de ressources)](../../../framework/tools/resgen-exe-resource-file-generator.md) ou dans l’environnement de développement, il est accessible avec <xref:System.Resources> les membres de l’espace de noms. (Pour plus d'informations, consultez <xref:System.Resources.ResourceManager>.) Pour accéder à toutes les autres ressources au moment de l’exécution, utilisez les `GetManifestResource` méthodes qui <xref:System.Reflection.Assembly> commencent par dans la classe.  
  
 Le nom de fichier peut être n’importe quel format de fichier. C’est le cas, par exemple, si vous voulez qu’une DLL native fasse partie de l'assembly pour qu’elle puisse être installée dans le Global Assembly Cache et accessible à partir du code managé dans l'assembly.  
  
 La forme abrégée de `-linkresource` est `-linkres`.  
  
> [!NOTE]
> L' `-linkresource` option n’est pas disponible dans l’environnement de développement Visual Studio; elle est disponible uniquement quand vous compilez à partir de la ligne de commande.  
  
## <a name="example"></a>Exemple  
 Le code suivant compile `in.vb` et établit un lien vers le fichier `rf.resource`de ressources.  
  
```console  
vbc -linkresource:rf.resource in.vb  
```  
  
## <a name="see-also"></a>Voir aussi

- [Compilateur de ligne de commande de Visual Basic](../../../visual-basic/reference/command-line-compiler/index.md)
- [-cible (Visual Basic)](../../../visual-basic/reference/command-line-compiler/target.md)
- [-ressource (Visual Basic)](../../../visual-basic/reference/command-line-compiler/resource.md)
- [Exemples de lignes de commande de compilation](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
