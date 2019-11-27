---
title: -resource
ms.date: 03/13/2018
helpviewer_keywords:
- /resource compiler option [Visual Basic]
- -resource compiler option [Visual Basic]
- /res compiler option [Visual Basic]
- res compiler option [Visual Basic]
- -res compiler option [Visual Basic]
- resource compiler option [Visual Basic]
ms.assetid: eee2f227-91f2-4f2b-a9d6-1c51c5320858
ms.openlocfilehash: a781d543dd32ffb3d0ac0b11c544dbfd8cd5d806
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74348565"
---
# <a name="-resource-visual-basic"></a>-ressource (Visual Basic)
Incorpore une ressource managée dans un assembly.  
  
## <a name="syntax"></a>Syntaxe  
  
```console  
-resource:filename[,identifier[,public|private]]  
```

or  

```console
-res:filename[,identifier[,public|private]]  
```  
  
## <a name="arguments"></a>Arguments  
  
|Terme|Définition|  
|---|---|  
|`filename`|Requis. Nom du fichier de ressources à incorporer dans le fichier de sortie. Par défaut, `filename` est public dans l’assembly. Placez le nom de fichier entre guillemets ("") s’il contient un espace.|  
|`identifier`|Ce paramètre est facultatif. Nom logique de la ressource ; nom utilisé pour le charger. La valeur par défaut est le nom du fichier. Si vous le souhaitez, vous pouvez spécifier si la ressource est publique ou privée dans le manifeste de l’assembly, comme dans l’exemple suivant : `-res:filename.res, myname.res, public`|  
  
## <a name="remarks"></a>Notes  
 Utilisez `-linkresource` pour lier une ressource à un assembly sans placer le fichier de ressources dans le fichier de sortie.  
  
 Si `filename` est un fichier de ressources .NET Framework créé, par exemple, par [Resgen. exe (générateur de fichiers de ressources)](../../../framework/tools/resgen-exe-resource-file-generator.md) ou dans l’environnement de développement, il est accessible à l’aide des membres de l’espace de noms <xref:System.Resources> (pour plus d’informations, consultez <xref:System.Resources.ResourceManager>). Pour accéder à toutes les autres ressources au moment de l’exécution, utilisez l’une des méthodes suivantes : <xref:System.Reflection.Assembly.GetManifestResourceInfo%2A>, <xref:System.Reflection.Assembly.GetManifestResourceNames%2A>ou <xref:System.Reflection.Assembly.GetManifestResourceStream%2A>.  
  
 La forme abrégée de `-resource` est `-res`.  
  
 Pour plus d’informations sur la façon de définir `-resource` dans l’IDE de Visual Studio, consultez [gestion des ressources d’application (.net)](/visualstudio/ide/managing-application-resources-dotnet).  
  
## <a name="example"></a>Exemple  
 Le code suivant compile `In.vb` et joint le `Rf.resource`de fichier de ressources.  
  
```console
vbc -res:rf.resource in.vb  
```  
  
## <a name="see-also"></a>Voir aussi

- [Compilateur de ligne de commande de Visual Basic](../../../visual-basic/reference/command-line-compiler/index.md)
- [-win32resource](../../../visual-basic/reference/command-line-compiler/win32resource.md)
- [-linkresource (Visual Basic)](../../../visual-basic/reference/command-line-compiler/linkresource.md)
- [-cible (Visual Basic)](../../../visual-basic/reference/command-line-compiler/target.md)
- [Exemples de lignes de commande de compilation](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
