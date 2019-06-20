---
title: -sdkpath
ms.date: 07/20/2015
f1_keywords:
- sdkpath
- -sdkpath
helpviewer_keywords:
- -sdkpath compiler option [Visual Basic]
- /sdkpath compiler option [Visual Basic]
- sdkpath compiler option [Visual Basic]
ms.assetid: fec8a3f1-b791-4a37-8af7-344859f8212d
ms.openlocfilehash: 91f64756b2fbf14dc96550420cd936973e6bec87
ms.sourcegitcommit: 4c41ec195caf03d98b7900007c3c8e24eba20d34
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/20/2019
ms.locfileid: "67268296"
---
# <a name="-sdkpath"></a>-sdkpath
Spécifie l’emplacement de mscorlib.dll et de Microsoft.VisualBasic.dll.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
-sdkpath:path  
```  
  
## <a name="arguments"></a>Arguments  
 `path`  
 Le répertoire contenant les versions de mscorlib.dll et de Microsoft.VisualBasic.dll à utiliser pour la compilation. Ce chemin d’accès n’est pas vérifié jusqu'à ce qu’il est chargé. Placez le nom de répertoire entre guillemets ( » «) s’il contient un espace.  
  
## <a name="remarks"></a>Notes  
 Cette option indique au compilateur de Visual Basic pour charger le mscorlib.dll et Microsoft.VisualBasic.dll fichiers à partir d’un emplacement non défini par défaut. Le `-sdkpath` option a été conçue pour être utilisée avec [- /netcf](../../../visual-basic/reference/command-line-compiler/netcf.md). Le .NET Compact Framework utilise différentes versions de ces bibliothèques d’assistance pour éviter l’utilisation de types et les fonctionnalités de langage introuvables sur les appareils.  
  
> [!NOTE]
>  Le `-sdkpath` option n’est pas disponible dans l’environnement de développement Visual Studio ; il est disponible uniquement lors de la compilation à partir de la ligne de commande. Le `-sdkpath` option est définie lorsqu’un projet smart device de Visual Basic est chargé.  
  
 Vous pouvez spécifier que le compilateur doit compiler sans référence à la bibliothèque Runtime Visual Basic à l’aide de la `-vbruntime` option du compilateur. Pour plus d’informations, consultez [- vbruntime](../../../visual-basic/reference/command-line-compiler/vbruntime.md).  
  
## <a name="example"></a>Exemple  
 Le code suivant compile `Myfile.vb` avec .NET Compact Framework, l’utilisation des versions de Mscorlib.dll et de Microsoft.VisualBasic.dll trouvées dans le répertoire d’installation par défaut du .NET Compact Framework sur le lecteur C. En règle générale, vous utiliseriez la version la plus récente du .NET Compact Framework.  
  
```console
vbc -netcf -sdkpath:"c:\Program Files\Microsoft Visual Studio .NET 2003\CompactFrameworkSDK\v1.0.5000\Windows CE " myfile.vb  
```  
  
## <a name="see-also"></a>Voir aussi

- [Compilateur de ligne de commande de Visual Basic](../../../visual-basic/reference/command-line-compiler/index.md)
- [Exemples de lignes de commande de compilation](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
- [-netcf](../../../visual-basic/reference/command-line-compiler/netcf.md)
- [-vbruntime](../../../visual-basic/reference/command-line-compiler/vbruntime.md)
