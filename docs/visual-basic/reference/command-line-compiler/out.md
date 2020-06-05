---
title: -out
ms.date: 07/20/2015
helpviewer_keywords:
- /out compiler option [Visual Basic]
- -out compiler option [Visual Basic]
- out compiler option [Visual Basic]
ms.assetid: 9f148c15-0909-4cb8-a2db-777f8a8b45ae
ms.openlocfilehash: 75f3ee7f24112f911803732ccb8d39eeafa95e3d
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84400511"
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
 Spécifiez le nom complet et l’extension du fichier à créer. Si vous ne le faites pas, le fichier. exe utilise son nom dans le fichier de code source contenant la `Sub Main` procédure, et le fichier. dll prend son nom dans le premier fichier de code source.  
  
 Si vous spécifiez un nom de fichier sans extension. exe ou. dll, le compilateur ajoute automatiquement l’extension pour vous, en fonction de la valeur spécifiée pour l' `-target` option du compilateur.  
  
|Pour définir l’environnement de développement intégré de Visual Studio|  
|---|  
|1. Sélectionnez un projet dans **Explorateur de solutions**. Dans le menu **Projet** , cliquez sur **Propriétés**. <br />2. cliquez sur l’onglet **application** .<br />3. modifiez la valeur dans la zone nom de l' **assembly** .|  
  
## <a name="example"></a>Exemple  
 Le code suivant compile `T2.vb` et crée le fichier de sortie `T2.exe` .  
  
```console
vbc t2.vb -out:t3.exe  
```  
  
## <a name="see-also"></a>Voir aussi

- [Compilateur de ligne de commande de Visual Basic](index.md)
- [-cible (Visual Basic)](target.md)
- [Exemples de lignes de commande de compilation](sample-compilation-command-lines.md)
