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
ms.openlocfilehash: ce1f24f25ea58cb6ddc2f5c582b6103d8f18d922
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/23/2020
ms.locfileid: "91085163"
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
|`+` &#124; `-`|Optionnel. `-removeintchecks-`Avec l’option, le compilateur vérifie tous les calculs d’entiers pour les erreurs de dépassement de capacité. La valeur par défaut est `-removeintchecks-`.<br /><br /> Le `-removeintchecks` fait de spécifier ou d' `-removeintchecks+` empêcher la vérification des erreurs et peut accélérer le calcul des entiers. Toutefois, sans vérification des erreurs, et si les capacités des types de données sont dépassées, des résultats incorrects peuvent être stockés sans déclencher d’erreur.|  
  
|Pour définir-removeintchecks (dans l’environnement de développement intégré Visual Studio|  
|---|  
|1. Sélectionnez un projet dans **Explorateur de solutions**. Dans le menu **Projet** , cliquez sur **Propriétés**. <br />2. cliquez sur l’onglet **compiler** .<br />3. cliquez sur le bouton **avancé** .<br />4. modifiez la valeur de la zone supprimer les contrôles de dépassement sur les **entiers** .|  
  
## <a name="example"></a>Exemple  

 Le code suivant compile `Test.vb` et désactive la vérification des erreurs de dépassement sur les entiers.  
  
```console
vbc -removeintchecks+ test.vb  
```  
  
## <a name="see-also"></a>Voir aussi

- [Compilateur de ligne de commande de Visual Basic](index.md)
- [Exemples de lignes de commande de compilation](sample-compilation-command-lines.md)
