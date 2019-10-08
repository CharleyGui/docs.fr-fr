---
title: -out (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- /out compiler option [Visual Basic]
- -out compiler option [Visual Basic]
- out compiler option [Visual Basic]
ms.assetid: 9f148c15-0909-4cb8-a2db-777f8a8b45ae
ms.openlocfilehash: 6b005ac26e3fffad350cb4ce52f7757c9fff2ac1
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/07/2019
ms.locfileid: "72005331"
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
 Spécifiez le nom complet et l’extension du fichier à créer. Si vous ne le faites pas, le fichier. exe utilise son nom dans le fichier de code source contenant la procédure `Sub Main`, et le fichier. dll prend son nom dans le premier fichier de code source.  
  
 Si vous spécifiez un nom de fichier sans extension. exe ou. dll, le compilateur ajoute automatiquement l’extension pour vous, en fonction de la valeur spécifiée pour l’option du compilateur `-target`.  
  
|Pour définir l’environnement de développement intégré de Visual Studio|  
|---|  
|1.  Sélectionnez un projet dans l' **Explorateur de solutions**. Dans le menu **Projet**, cliquez sur **Propriétés**. <br />2.  Cliquez sur l’onglet **Application** .<br />3.  Modifiez la valeur dans la zone nom de l' **assembly** .|  
  
## <a name="example"></a>Exemple  
 Le code suivant compile `T2.vb` et crée le fichier de sortie `T2.exe`.  
  
```console
vbc t2.vb -out:t3.exe  
```  
  
## <a name="see-also"></a>Voir aussi

- [Compilateur de ligne de commande de Visual Basic](../../../visual-basic/reference/command-line-compiler/index.md)
- [-cible (Visual Basic)](../../../visual-basic/reference/command-line-compiler/target.md)
- [Exemples de lignes de commande de compilation](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
