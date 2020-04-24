---
title: -vbruntime
ms.date: 03/13/2018
f1_keywords:
- vbruntime
- -vbruntime
helpviewer_keywords:
- vbruntime compiler option [Visual Basic]
- -vbruntime compiler option [Visual Basic]
- /vbruntime compiler option [Visual Basic]
ms.assetid: 1aa0239e-511a-4c29-957d-fd72877b350a
ms.openlocfilehash: 8c7789c6af7b82ecb40ecd73d09f64aa1da3fd4b
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/07/2019
ms.locfileid: "72005051"
---
# <a name="-vbruntime"></a>-vbruntime
Spécifie que le compilateur doit compiler sans référence à la bibliothèque runtime Visual Basic, ou avec une référence à une bibliothèque runtime spécifique.  
  
## <a name="syntax"></a>Syntaxe  
  
```console  
-vbruntime:{ - | + | * | path }  
```  
  
## <a name="arguments"></a>Arguments  
 \-  
 Compilez sans référence à la bibliothèque Runtime Visual Basic.  
  
 \+  
 Compilez avec une référence à la bibliothèque Visual Basic Runtime par défaut.  
  
 \*  
 Compilez sans une référence à la bibliothèque Runtime Visual Basic et incorporez les fonctionnalités principales de la bibliothèque Visual Basic Runtime dans l’assembly.  
  
 `path`  
 Compilez avec une référence à la bibliothèque (DLL) spécifiée.  
  
## <a name="remarks"></a>Notes  
 L' `-vbruntime` option de compilateur vous permet de spécifier que le compilateur doit compiler sans référence à la bibliothèque d’exécution Visual Basic. Si vous compilez sans une référence à la bibliothèque Runtime Visual Basic, des erreurs ou des avertissements sont enregistrés dans les constructions de code ou de langage qui génèrent un appel à une application auxiliaire Visual Basic Runtime. (Une *Visual Basic Helper du runtime* est une fonction définie dans Microsoft. VisualBasic. dll qui est appelée au moment de l’exécution pour exécuter une sémantique de langage spécifique.)  
  
 L' `-vbruntime+` option produit le même comportement qui se produit si `-vbruntime` aucun commutateur n’est spécifié. Vous pouvez utiliser l' `-vbruntime+` option pour remplacer les commutateurs précédents `-vbruntime` .  
  
 La plupart des objets `My` du type ne sont pas disponibles lorsque vous `-vbruntime-` utilisez `-vbruntime:path` les options ou.  
  
## <a name="embedding-visual-basic-runtime-core-functionality"></a>Incorporation des fonctionnalités principales du runtime d’Visual Basic  
 L' `-vbruntime*` option vous permet de compiler sans référence à une bibliothèque Runtime. Au lieu de cela, les fonctionnalités principales de la bibliothèque Runtime Visual Basic sont incorporées dans l’assembly utilisateur. Vous pouvez utiliser cette option si votre application s’exécute sur des plateformes qui ne contiennent pas le runtime Visual Basic.  
  
 Les membres du runtime suivants sont incorporés :  
  
- Classe <xref:Microsoft.VisualBasic.CompilerServices.Conversions>  
  
- Méthode <xref:Microsoft.VisualBasic.Strings.AscW%28System.Char%29>  
  
- Méthode <xref:Microsoft.VisualBasic.Strings.AscW%28System.String%29>  
  
- Méthode <xref:Microsoft.VisualBasic.Strings.ChrW%28System.Int32%29>  
  
- <xref:Microsoft.VisualBasic.Constants.vbBack>suivantes  
  
- <xref:Microsoft.VisualBasic.Constants.vbCr>suivantes  
  
- <xref:Microsoft.VisualBasic.Constants.vbCrLf>suivantes  
  
- <xref:Microsoft.VisualBasic.Constants.vbFormFeed>suivantes  
  
- <xref:Microsoft.VisualBasic.Constants.vbLf>suivantes  
  
- <xref:Microsoft.VisualBasic.Constants.vbNewLine>suivantes  
  
- <xref:Microsoft.VisualBasic.Constants.vbNullChar>suivantes  
  
- <xref:Microsoft.VisualBasic.Constants.vbNullString>suivantes  
  
- <xref:Microsoft.VisualBasic.Constants.vbTab>suivantes  
  
- <xref:Microsoft.VisualBasic.Constants.vbVerticalTab>suivantes  
  
- Certains objets du `My` type  
  
 Si vous compilez `-vbruntime*` à l’aide de l’option et que votre code fait référence à un membre de la bibliothèque d’exécution Visual Basic qui n’est pas incorporée avec la fonctionnalité de base, le compilateur retourne une erreur qui indique que le membre n’est pas disponible.  
  
## <a name="referencing-a-specified-library"></a>Référencement d’une bibliothèque spécifiée  
 Vous pouvez utiliser l' `path` argument pour compiler avec une référence à une bibliothèque Runtime personnalisée au lieu de la bibliothèque Visual Basic Runtime par défaut.  
  
 Si la valeur de l' `path` argument est un chemin d’accès qualifié complet à une dll, le compilateur utilise ce fichier comme bibliothèque Runtime. Si la valeur de l' `path` argument n’est pas un chemin d’accès complet à une dll, le compilateur Visual Basic recherche d’abord la DLL identifiée dans le dossier actif. Il effectue ensuite une recherche dans le chemin d’accès que vous avez spécifié à l’aide de l’option [de compilateur-sdkpath](../../../visual-basic/reference/command-line-compiler/sdkpath.md) . Si l' `-sdkpath` option de compilateur n’est pas utilisée, le compilateur recherche la DLL identifiée dans le dossier .NET Framework`%systemroot%\Microsoft.NET\Framework\versionNumber`().  
  
## <a name="example"></a>Exemple  
 L’exemple suivant montre comment utiliser l' `-vbruntime` option pour compiler avec une référence à une bibliothèque personnalisée.  
  
```console
vbc -vbruntime:C:\VBLibraries\CustomVBLibrary.dll  
```  
  
## <a name="see-also"></a>Voir aussi

- [Visual Basic Core – nouveau mode de compilation dans Visual Studio 2010 SP1](https://devblogs.microsoft.com/vbteam/vb-core-new-compilation-mode-in-visual-studio-2010-sp1/)
- [Compilateur de ligne de commande de Visual Basic](../../../visual-basic/reference/command-line-compiler/index.md)
- [Exemples de lignes de commande de compilation](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
- [-sdkpath](../../../visual-basic/reference/command-line-compiler/sdkpath.md)
