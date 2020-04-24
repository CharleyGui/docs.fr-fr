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
ms.openlocfilehash: 46cec7ac3cb78c4fc97e299535f9085eff6daeff
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/07/2019
ms.locfileid: "72004692"
---
# <a name="-sdkpath"></a>-sdkpath
Spécifie l’emplacement de mscorlib. dll et de Microsoft. VisualBasic. dll.  
  
## <a name="syntax"></a>Syntaxe  
  
```console  
-sdkpath:path  
```  
  
## <a name="arguments"></a>Arguments  
 `path`  
 Répertoire contenant les versions de mscorlib. dll et de Microsoft. VisualBasic. dll à utiliser pour la compilation. Ce chemin d’accès n’est pas vérifié tant qu’il n’est pas chargé. Placez le nom du répertoire entre guillemets ("") s’il contient un espace.  
  
## <a name="remarks"></a>Notes  
 Cette option indique au compilateur Visual Basic de charger les fichiers Mscorlib. dll et Microsoft. VisualBasic. dll à partir d’un emplacement autre que celui par défaut. L' `-sdkpath` option a été conçue pour être utilisée avec [-netcf](../../../visual-basic/reference/command-line-compiler/netcf.md). Le .NET Compact Framework utilise différentes versions de ces bibliothèques de prise en charge pour éviter l’utilisation de types et de fonctionnalités de langage introuvables sur les appareils.  
  
> [!NOTE]
> L' `-sdkpath` option n’est pas disponible dans l’environnement de développement Visual Studio. elle est disponible uniquement lors de la compilation à partir de la ligne de commande. L' `-sdkpath` option est définie lors du chargement d’un projet d’appareil Visual Basic.  
  
 Vous pouvez spécifier que le compilateur doit compiler sans référence à la bibliothèque Visual Basic Runtime à l’aide de `-vbruntime` l’option du compilateur. Pour plus d’informations, consultez [-vbruntime](../../../visual-basic/reference/command-line-compiler/vbruntime.md).  
  
## <a name="example"></a>Exemple  
 Le code suivant est compilé `Myfile.vb` avec l' .NET Compact Framework, à l’aide des versions de mscorlib. dll et de Microsoft. VisualBasic. dll trouvées dans le répertoire d’installation par défaut du .NET Compact Framework sur le lecteur C. En règle générale, vous utilisez la version la plus récente du .NET Compact Framework.  
  
```console
vbc -netcf -sdkpath:"c:\Program Files\Microsoft Visual Studio .NET 2003\CompactFrameworkSDK\v1.0.5000\Windows CE " myfile.vb  
```  
  
## <a name="see-also"></a>Voir aussi

- [Compilateur de ligne de commande de Visual Basic](../../../visual-basic/reference/command-line-compiler/index.md)
- [Exemples de lignes de commande de compilation](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
- [-netcf](../../../visual-basic/reference/command-line-compiler/netcf.md)
- [-vbruntime](../../../visual-basic/reference/command-line-compiler/vbruntime.md)
