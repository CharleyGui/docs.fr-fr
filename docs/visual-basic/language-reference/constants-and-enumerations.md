---
title: Constantes et énumérations (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- enumerations [Visual Basic]
- constants [Visual Basic]
- constants [Visual Basic], list of
ms.assetid: 309c0ad5-83e4-4f96-99ea-83cd95107417
ms.openlocfilehash: ec314f78cf4c22c39d1ce41a7623bb4891f6ecd0
ms.sourcegitcommit: 559259da2738a7b33a46c0130e51d336091c2097
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72774857"
---
# <a name="constants-and-enumerations-visual-basic"></a>Constantes et énumérations (Visual Basic)
Visual Basic fournit un certain nombre de constantes et d’énumérations prédéfinies pour les développeurs. Les constantes stockent des valeurs qui restent constantes tout au long de l’exécution d’une application. Les énumérations offrent un moyen pratique de travailler avec des ensembles de constantes connexes et d’associer des valeurs de constantes à des noms.  
  
## <a name="constants"></a>Constantes  
  
### <a name="conditional-compilation-constants"></a>Constantes de compilation conditionnelle  
 Le tableau suivant répertorie les constantes prédéfinies disponibles pour la compilation conditionnelle.  
  
|**Constante**|**Description**|  
|---|---|  
|`CONFIG`|Chaîne qui correspond au paramètre actuel de la zone de **configuration de la solution active** dans la **Configuration Manager**.|  
|`DEBUG`|Valeur `Boolean` qui peut être définie dans la boîte de dialogue **Propriétés du projet** . Par défaut, la configuration de débogage d’un projet définit `DEBUG`. Lorsque `DEBUG` est défini, <xref:System.Diagnostics.Debug> méthodes de classe génèrent une sortie dans la fenêtre **sortie** . Quand il n’est pas défini, les méthodes de classe <xref:System.Diagnostics.Debug> ne sont pas compilées et aucune sortie de débogage n’est générée.|  
|`TARGET`|Chaîne représentant le type de sortie du projet ou le paramètre de l’option **/target** de la ligne de commande. Les valeurs possibles de `TARGET` sont les suivantes :<br /><br /> -« winexe » pour une application Windows.<br />-« exe » pour une application console.<br />-« Library » pour une bibliothèque de classes.<br />-« module » pour un module.<br />-L’option **/target** peut être définie dans l’environnement de développement intégré de Visual Studio. Pour plus d’informations, consultez [-target (Visual Basic)](../../visual-basic/reference/command-line-compiler/target.md).|  
|`TRACE`|Valeur `Boolean` qui peut être définie dans la boîte de dialogue **Propriétés du projet** . Par défaut, toutes les configurations d’un projet définissent `TRACE`. Lorsque `TRACE` est défini, <xref:System.Diagnostics.Trace> méthodes de classe génèrent une sortie dans la fenêtre **sortie** . Quand il n’est pas défini, les méthodes de classe <xref:System.Diagnostics.Trace> ne sont pas compilées et aucune sortie de `Trace` n’est générée.|  
|`VBC_VER`|Nombre représentant la version de Visual Basic, dans *major*. format *mineur* .|  
  
### <a name="print-and-display-constants"></a>Constantes d’impression et d’affichage  
 Lorsque vous appelez les fonctions d’impression et d’affichage, vous pouvez utiliser les constantes suivantes dans votre code à la place des valeurs réelles.  
  
|**Constante**|**Description**|  
|---|---|  
|`vbCrLf`|Combinaison de caractères retour chariot/saut de ligne.|  
|`vbCr`|Caractère de retour chariot.|  
|`vbLf`|Caractère de saut de ligne.|  
|`vbNewLine`|Caractère de saut de ligne.|  
|`vbNullChar`|Caractère null.|  
|`vbNullString`|Différent d’une chaîne de longueur nulle (""); utilisé pour appeler des procédures externes.|  
|`vbObjectError`|Numéro d'erreur. Les numéros d’erreur définis par l’utilisateur doivent être supérieurs à cette valeur. Exemple :<br /><br /> `Err.Raise(Number) = vbObjectError + 1000`|  
|`vbTab`|Caractère de tabulation.|  
|`vbBack`|Caractère de retour arrière.|  
|`vbFormFeed`|Non utilisé dans Microsoft Windows.|  
|`vbVerticalTab`|Non utile dans Microsoft Windows.|  
  
## <a name="enumerations"></a>Énumérations  
 Le tableau suivant répertorie et décrit les énumérations fournies par Visual Basic.  
  
|Énumération|Description|  
|---|---|  
|<xref:Microsoft.VisualBasic.AppWinStyle>|Indique le style de fenêtre à utiliser pour le programme appelé lors de l’appel de la fonction <xref:Microsoft.VisualBasic.Interaction.Shell%2A>.|  
|<xref:Microsoft.VisualBasic.AudioPlayMode>|Indique comment lire des sons lors de l’appel de méthodes audio.|  
|<xref:Microsoft.VisualBasic.ApplicationServices.BuiltInRole>|Indique le type de rôle à vérifier lors de l’appel de la méthode <xref:Microsoft.VisualBasic.ApplicationServices.User.IsInRole%2A>.|  
|<xref:Microsoft.VisualBasic.CallType>|Indique le type de procédure qui est appelé lors de l’appel de la fonction <xref:Microsoft.VisualBasic.Interaction.CallByName%2A>.|  
|<xref:Microsoft.VisualBasic.CompareMethod>|Indique comment comparer des chaînes lors de l’appel de fonctions de comparaison.|  
|<xref:Microsoft.VisualBasic.DateFormat>|Indique comment afficher les dates lors de l’appel de la fonction <xref:Microsoft.VisualBasic.Strings.FormatDateTime%2A>.|  
|<xref:Microsoft.VisualBasic.DateInterval>|Indique comment déterminer et mettre en forme les intervalles de date pendant l’appel des fonctions de date.|  
|<xref:Microsoft.VisualBasic.FileIO.DeleteDirectoryOption>|Spécifie ce qui doit être fait lorsqu’un répertoire à supprimer contient des fichiers ou des répertoires.|  
|<xref:Microsoft.VisualBasic.DueDate>|Indique à quel moment les paiements sont dus lors de l’appel de méthodes financières.|  
|<xref:Microsoft.VisualBasic.FileIO.FieldType>|Indique si les champs de texte sont délimités ou à largeur fixe.|  
|<xref:Microsoft.VisualBasic.FileAttribute>|Indique les attributs de fichier à utiliser lors de l’appel de fonctions d’accès au fichier.|  
|<xref:Microsoft.VisualBasic.FirstDayOfWeek>|Indique le premier jour de la semaine à utiliser lors de l’appel de fonctions liées à la date.|  
|<xref:Microsoft.VisualBasic.FirstWeekOfYear>|Indique la première semaine de l’année à utiliser lors de l’appel de fonctions liées à la date.|  
|<xref:Microsoft.VisualBasic.MsgBoxResult>|Indique le bouton qui a été enfoncé dans une boîte de message, retourné par la fonction <xref:Microsoft.VisualBasic.Interaction.MsgBox%2A>.|  
|<xref:Microsoft.VisualBasic.MsgBoxStyle>|Indique les boutons à afficher lors de l’appel de la fonction <xref:Microsoft.VisualBasic.Interaction.MsgBox%2A>.|  
|<xref:Microsoft.VisualBasic.OpenAccess>|Indique comment ouvrir un fichier lors de l’appel de fonctions d’accès au fichier.|  
|<xref:Microsoft.VisualBasic.OpenMode>|Indique comment ouvrir un fichier lors de l’appel de fonctions d’accès au fichier.|  
|<xref:Microsoft.VisualBasic.OpenShare>|Indique comment ouvrir un fichier lors de l’appel de fonctions d’accès au fichier.|  
|<xref:Microsoft.VisualBasic.FileIO.RecycleOption>|Spécifie si un fichier doit être supprimé définitivement ou être placé dans la corbeille.|  
|<xref:Microsoft.VisualBasic.FileIO.SearchOption>|Spécifie s’il faut rechercher tous les répertoires de niveau supérieur ou uniquement.|  
|<xref:Microsoft.VisualBasic.TriState>|Indique une valeur de `Boolean` ou si la valeur par défaut doit être utilisée lors de l’appel de fonctions de mise en forme des nombres.|  
|<xref:Microsoft.VisualBasic.FileIO.UICancelOption>|Spécifie ce qui doit être fait si l’utilisateur clique sur **Annuler** pendant une opération.|  
|<xref:Microsoft.VisualBasic.FileIO.UIOption>|Spécifie s’il faut afficher une boîte de dialogue de progression lors de la copie, de la suppression ou du déplacement de fichiers ou de répertoires.|  
|<xref:Microsoft.VisualBasic.VariantType>|Indique le type d’un objet variant, retourné par la fonction <xref:Microsoft.VisualBasic.Information.VarType%2A>.|  
|<xref:Microsoft.VisualBasic.VbStrConv>|Indique le type de conversion à exécuter lors de l’appel de la fonction <xref:Microsoft.VisualBasic.Strings.StrConv%2A>.|  
  
## <a name="see-also"></a>Voir aussi

- [Informations de référence sur le langage Visual Basic](../../visual-basic/language-reference/index.md)
- [Visual Basic](../../visual-basic/index.md)
- [Vue d’ensemble des constantes](../../visual-basic/programming-guide/language-features/constants-enums/constants-overview.md)
- [Vue d’ensemble des énumérations](../../visual-basic/programming-guide/language-features/constants-enums/enumerations-overview.md)
