---
title: -warnaserror
ms.date: 03/13/2018
helpviewer_keywords:
- warnaserror compiler option [Visual Basic]
- /warnaserror compiler option [Visual Basic]
- -warnaserror compiler option [Visual Basic]
ms.assetid: 49819f1d-a1bd-4201-affe-5afe6d9712e1
ms.openlocfilehash: 2c243b05b7e819691165ef20996691c0bd38ae4a
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/23/2020
ms.locfileid: "91098863"
---
# <a name="-warnaserror-visual-basic"></a>-warnaserror (Visual Basic)

Indique au compilateur de considérer la première occurrence d’un avertissement comme une erreur.  
  
## <a name="syntax"></a>Syntaxe  
  
```console  
-warnaserror[+ | -][:numberList]  
```  
  
## <a name="arguments"></a>Arguments  
  
|Terme|Définition|  
|---|---|  
|+ &#124; -|Optionnel. Par défaut, `-warnaserror-` est en vigueur ; les avertissements n’empêchent pas le compilateur de produire un fichier de sortie. Du fait de l’option `-warnaserror`, qui est identique à `-warnaserror+`, les avertissements sont considérés comme des erreurs.|  
|`numberList`|Optionnel. Liste délimitée par des virgules des numéros d’ID d’avertissement auxquels l’option `-warnaserror` s’applique. Si aucun ID d’avertissement n’est spécifié, l’option `-warnaserror` s’applique à tous les avertissements.|  
  
## <a name="remarks"></a>Notes  

 L’option `-warnaserror` considère tous les avertissements comme des erreurs. Les messages qui d’ordinaire sont signalés comme des avertissements s’affichent en tant qu’erreurs. Le compilateur signale les occurrences suivantes du même avertissement comme des avertissements.  
  
 Par défaut, `-warnaserror-` est en vigueur. Les avertissements sont donc uniquement à caractère informatif. Du fait de l’option `-warnaserror`, qui est identique à `-warnaserror+`, les avertissements sont considérés comme des erreurs.  
  
 Si vous voulez que seuls certains avertissements spécifiques soient considérés comme des erreurs, vous pouvez spécifier une liste séparée par des virgules qui liste les numéros d’avertissement à considérer comme des erreurs.  
  
> [!NOTE]
> L’option `-warnaserror` ne contrôle pas le mode d’affichage des avertissements. Utilisez l’option [-nowarn](nowarn.md) pour désactiver les avertissements.  
  
|Pour définir -warnaserror de manière à considérer tous les avertissements comme des erreurs dans l’IDE Visual Studio|  
|---|  
|1. Sélectionnez un projet dans **Explorateur de solutions**. Dans le menu **Projet** , cliquez sur **Propriétés**. <br />2. cliquez sur l’onglet **compiler** .<br />3. Assurez-vous que la case à cocher **Désactiver tous les avertissements** est désactivée.<br />4. activez la case à cocher **considérer tous les avertissements comme des erreurs** .|  
  
|Pour définir -warnaserror de manière à considérer certains avertissements comme des erreurs dans l’IDE Visual Studio|  
|---|  
|1. Sélectionnez un projet dans **Explorateur de solutions**. Dans le menu **Projet** , cliquez sur **Propriétés**.<br />2. cliquez sur l’onglet **compiler** .<br />3. Assurez-vous que la case à cocher **Désactiver tous les avertissements** est désactivée.<br />4. Assurez-vous que la case à cocher **considérer tous les avertissements comme des erreurs** est désactivée.<br />5. Sélectionnez **erreur** dans la colonne **notification** adjacente à l’avertissement qui doit être traité comme une erreur.|  
  
## <a name="example"></a>Exemple  

 Le code suivant compile `In.vb` et indique au compilateur d’afficher une erreur à la première occurrence de chaque avertissement rencontré.  
  
```console
vbc -warnaserror in.vb  
```  
  
## <a name="example"></a>Exemple  

 Le code suivant compile `T2.vb` et considère uniquement l’avertissement pour les variables locales inutilisées (42024) comme une erreur.  
  
```console
vbc -warnaserror:42024 t2.vb  
```  
  
## <a name="see-also"></a>Voir aussi

- [Compilateur de ligne de commande de Visual Basic](index.md)
- [Exemples de lignes de commande de compilation](sample-compilation-command-lines.md)
- [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic)
