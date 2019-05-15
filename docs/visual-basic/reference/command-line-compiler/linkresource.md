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
ms.openlocfilehash: 637a1d4b7a523feb2fc8da10a0c18e68774c480a
ms.sourcegitcommit: c7a7e1468bf0fa7f7065de951d60dfc8d5ba89f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/14/2019
ms.locfileid: "65586697"
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
 Obligatoire. Le fichier de ressources à lier à l’assembly. Si le nom de fichier contient un espace, placez le nom entre guillemets ( » «).  
  
 `identifier`  
 Facultatif. Le nom logique pour la ressource. Le nom qui est utilisé pour charger la ressource. La valeur par défaut est le nom du fichier. Si vous le souhaitez, vous pouvez spécifier si le fichier est public ou privé dans le manifeste d’assembly, par exemple : `-linkres:filename.res,myname.res,public`. Par défaut, `filename` est public dans l’assembly.  
  
## <a name="remarks"></a>Notes  
 Le `-linkresource` option ne pas incorpore le fichier de ressources dans le fichier de sortie ; Utilisez la `-resource` option pour ce faire.  
  
 Le `-linkresource` option requiert l’une de la `-target` autre que `-target:module`.  
  
 Si `filename` est un fichier de ressources .NET Framework créé, par exemple, par le [Resgen.exe (Resource File Generator)](../../../framework/tools/resgen-exe-resource-file-generator.md) ou dans l’environnement de développement, il est accessible à l’aide des membres de la <xref:System.Resources> espace de noms. (Pour plus d'informations, consultez <xref:System.Resources.ResourceManager>.) Pour accéder à toutes les autres ressources au moment de l’exécution, utilisez les méthodes qui commencent par `GetManifestResource` dans la <xref:System.Reflection.Assembly> classe.  
  
 Le nom de fichier peut être n’importe quel format de fichier. C’est le cas, par exemple, si vous voulez qu’une DLL native fasse partie de l'assembly pour qu’elle puisse être installée dans le Global Assembly Cache et accessible à partir du code managé dans l'assembly.  
  
 La forme abrégée de `-linkresource` est `-linkres`.  
  
> [!NOTE]
>  Le `-linkresource` option n’est pas disponible dans l’environnement de développement Visual Studio ; il est disponible uniquement lorsque vous compilez à partir de la ligne de commande.  
  
## <a name="example"></a>Exemple  
 Le code suivant compile `in.vb` et des liens vers le fichier de ressources `rf.resource`.  
  
```console  
vbc -linkresource:rf.resource in.vb  
```  
  
## <a name="see-also"></a>Voir aussi

- [Compilateur de ligne de commande de Visual Basic](../../../visual-basic/reference/command-line-compiler/index.md)
- [-target (Visual Basic)](../../../visual-basic/reference/command-line-compiler/target.md)
- [-resource (Visual Basic)](../../../visual-basic/reference/command-line-compiler/resource.md)
- [Exemples de lignes de commande de compilation](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
