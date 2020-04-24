---
title: -out
ms.date: 07/20/2015
helpviewer_keywords:
- /out compiler option [Visual Basic]
- -out compiler option [Visual Basic]
- out compiler option [Visual Basic]
ms.assetid: 9f148c15-0909-4cb8-a2db-777f8a8b45ae
ms.openlocfilehash: 67366e13e4dceea4772d0730222413cb25b4e8b7
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74352388"
---
# <a name="-out-visual-basic"></a>-out (Visual Basic)
Spécifie le nom du fichier de sortie.  
  
## <a name="syntax"></a>Syntaxe  
  
```console  
-out:filename  
```  
  
## <a name="arguments"></a>Arguments  
  
|Terme|Définition|  
|---|---|  
|`filename`|Obligatoire. Nom du fichier de sortie que le compilateur crée. Si le nom de fichier contient un espace, mettez-le entre guillemets ("").|  
  
## <a name="remarks"></a>Notes  
 Spécifiez le nom complet et l’extension du fichier à créer. Si vous ne le faites pas, le fichier. exe utilise son nom dans le fichier de code source `Sub Main` contenant la procédure, et le fichier. dll prend son nom dans le premier fichier de code source.  
  
 Si vous spécifiez un nom de fichier sans extension. exe ou. dll, le compilateur ajoute automatiquement l’extension pour vous, en fonction de la valeur spécifiée pour `-target` l’option du compilateur.  
  
|Pour définir l’environnement de développement intégré de Visual Studio|  
|---|  
|1. Sélectionnez un projet dans **Explorateur de solutions**. Dans le menu **Projet** , cliquez sur **Propriétés**. <br />2. cliquez sur l’onglet **application** .<br />3. modifiez la valeur dans la zone nom de l' **assembly** .|  
  
## <a name="example"></a>Exemple  
 Le code suivant compile `T2.vb` et crée le fichier `T2.exe`de sortie.  
  
```console
vbc t2.vb -out:t3.exe  
```  
  
## <a name="see-also"></a>Voir aussi

- [Compilateur de ligne de commande de Visual Basic](../../../visual-basic/reference/command-line-compiler/index.md)
- [-cible (Visual Basic)](../../../visual-basic/reference/command-line-compiler/target.md)
- [Exemples de lignes de commande de compilation](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
