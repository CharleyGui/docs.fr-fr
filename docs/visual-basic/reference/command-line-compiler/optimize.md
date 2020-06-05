---
title: -optimize
ms.date: 07/20/2015
helpviewer_keywords:
- optimize compiler option [Visual Basic]
- /optimize compiler option [Visual Basic]
- optimization [Visual Basic], enabling
- -optimize compiler option [Visual Basic]
ms.assetid: fcba4a97-3622-4b87-a891-0f77deab4998
ms.openlocfilehash: 337cb794ef9a405a178f1998cbe27b5da7709382
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84397439"
---
# <a name="-optimize"></a>-optimize
Active ou désactive les optimisations du compilateur.  
  
## <a name="syntax"></a>Syntaxe  
  
```console  
-optimize[ + | - ]  
```  
  
## <a name="arguments"></a>Arguments  
  
|Terme|Définition|  
|---|---|  
|`+` &#124; `-`|Facultatif. L' `-optimize-` option désactive les optimisations du compilateur. L' `-optimize+` option active les optimisations. Par défaut, les optimisations sont désactivées.|  
  
## <a name="remarks"></a>Notes  
 Les optimisations du compilateur diminuent la taille du fichier de sortie, le rendent plus rapide et plus efficace. Toutefois, étant donné que les optimisations entraînent une réorganisation du code dans le fichier de sortie, `-optimize+` peut compliquer le débogage.  
  
 Tous les modules générés avec `-target:module` pour un assembly doivent utiliser les mêmes `-optimize` paramètres que l’assembly. Pour plus d’informations, consultez [-target (Visual Basic)](target.md).  
  
 Vous pouvez combiner les `-optimize` `-debug` options et.  
  
|Pour définir-Optimize dans l’environnement de développement intégré Visual Studio|  
|---|  
|1. Sélectionnez un projet dans **Explorateur de solutions**. Dans le menu **Projet** , cliquez sur **Propriétés**.<br />     <br />2. cliquez sur l’onglet **compiler** .<br />3. cliquez sur le bouton **avancé** .<br />4. modifiez la case à cocher **activer les optimisations** .|  
  
## <a name="example"></a>Exemple  
 Le code suivant compile `T2.vb` et active les optimisations du compilateur.  
  
```console
vbc t2.vb -optimize  
```  
  
## <a name="see-also"></a>Voir aussi

- [Compilateur de ligne de commande de Visual Basic](index.md)
- [-Debug (Visual Basic)](debug.md)
- [Exemples de lignes de commande de compilation](sample-compilation-command-lines.md)
- [-cible (Visual Basic)](target.md)
