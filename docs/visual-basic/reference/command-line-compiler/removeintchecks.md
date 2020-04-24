---
title: -removeintchecks
ms.date: 03/13/2018
f1_keywords:
- removeintchecks
- -removeintchecks
helpviewer_keywords:
- removeintchecks compiler option [Visual Basic]
- /removeintchecks compiler option [Visual Basic]
- -removeintchecks compiler option [Visual Basic]
ms.assetid: c1835bd5-1e38-4fba-bd2f-6984774765d4
ms.openlocfilehash: bea6ca24ea6da9000267e754d52fe0ca152f7d7f
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/07/2019
ms.locfileid: "72005231"
---
# <a name="-removeintchecks"></a>-removeintchecks
Active ou désactive la vérification des erreurs de dépassement de capacité pour les opérations sur les entiers.  
  
## <a name="syntax"></a>Syntaxe  
  
```console  
-removeintchecks[+ | -]  
```  
  
## <a name="arguments"></a>Arguments  
  
|Terme|Définition|  
|---|---|  
|`+` &#124; `-`|Facultatif. Avec `-removeintchecks-` l’option, le compilateur vérifie tous les calculs d’entiers pour les erreurs de dépassement de capacité. Par défaut, il s’agit de `-removeintchecks-`.<br /><br /> Le `-removeintchecks` fait `-removeintchecks+` de spécifier ou d’empêcher la vérification des erreurs et peut accélérer le calcul des entiers. Toutefois, sans vérification des erreurs, et si les capacités des types de données sont dépassées, des résultats incorrects peuvent être stockés sans déclencher d’erreur.|  
  
|Pour définir-removeintchecks (dans l’environnement de développement intégré Visual Studio|  
|---|  
|1. Sélectionnez un projet dans **Explorateur de solutions**. Dans le menu **Projet** , cliquez sur **Propriétés**. <br />2. cliquez sur l’onglet **compiler** .<br />3. cliquez sur le bouton **avancé** .<br />4. modifiez la valeur de la zone supprimer les contrôles de dépassement sur les **entiers** .|  
  
## <a name="example"></a>Exemple  
 Le code suivant compile `Test.vb` et désactive la vérification des erreurs de dépassement sur les entiers.  
  
```console
vbc -removeintchecks+ test.vb  
```  
  
## <a name="see-also"></a>Voir aussi

- [Compilateur de ligne de commande de Visual Basic](../../../visual-basic/reference/command-line-compiler/index.md)
- [Exemples de lignes de commande de compilation](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
