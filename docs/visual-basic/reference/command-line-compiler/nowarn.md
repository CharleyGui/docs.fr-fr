---
title: -nowarn
ms.date: 07/20/2015
helpviewer_keywords:
- nowarn compiler option [Visual Basic]
- /nowarn compiler option [Visual Basic]
- -nowarn compiler option [Visual Basic]
ms.assetid: 7ebf2106-0652-4fdc-bf60-70fc86465d83
ms.openlocfilehash: 880fdf4931dadea547d64d0506bd3e978956468e
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/07/2019
ms.locfileid: "72005396"
---
# <a name="-nowarn"></a>-nowarn
Supprime la capacité du compilateur à générer des avertissements.  
  
## <a name="syntax"></a>Syntaxe  
  
```console  
-nowarn[:numberList]  
```  
  
## <a name="arguments"></a>Arguments  
  
|Terme|Définition|  
|---|---|  
|`numberList`|Facultatif. Liste délimitée par des virgules des numéros d’ID d’avertissement que le compilateur doit supprimer. Si les ID d’avertissement ne sont pas spécifiés, tous les avertissements sont supprimés.|  
  
## <a name="remarks"></a>Notes  
 Avec `-nowarn` l’option, le compilateur ne génère pas d’avertissements. Pour supprimer un avertissement individuel, fournissez l’ID d’avertissement `-nowarn` à l’option qui suit le signe deux-points. Séparez les numéros d’avertissement par des virgules.  
  
 Vous devez spécifier uniquement la partie numérique de l’identificateur d’avertissement. Par exemple, si vous souhaitez supprimer BC42024, l’avertissement pour les variables locales inutilisées, `-nowarn:42024`spécifiez.  
  
 Pour plus d’informations sur les numéros d’ID d’avertissement, consultez [Configuration des avertissements dans Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).  
  
|Pour définir-nowarn dans l’environnement de développement intégré de Visual Studio|  
|---|  
|1. Sélectionnez un projet dans **Explorateur de solutions**. Dans le menu **Projet** , cliquez sur **Propriétés**. <br />2. cliquez sur l’onglet **compiler** .<br />3. activez la case à cocher **Désactiver tous les avertissements** pour désactiver tous les avertissements.<br />     - ou -<br />     Pour désactiver un avertissement spécifique, cliquez sur **aucun** dans la liste déroulante adjacente à l’avertissement.|  
  
## <a name="example"></a>Exemple  
 Le code suivant compile `T2.vb` et n’affiche aucun avertissement.  
  
```console
vbc -nowarn t2.vb  
```  
  
## <a name="example"></a>Exemple  
 Le code suivant compile `T2.vb` et n’affiche pas les avertissements pour les variables locales inutilisées (42024).  
  
```console
vbc -nowarn:42024 t2.vb  
```  
  
## <a name="see-also"></a>Voir aussi

- [Compilateur de ligne de commande de Visual Basic](../../../visual-basic/reference/command-line-compiler/index.md)
- [Exemples de lignes de commande de compilation](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
- [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic)
