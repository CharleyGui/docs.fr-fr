---
title: Informations relatives à l'appelant
ms.date: 07/20/2015
ms.assetid: 15d556eb-4d0c-4497-98a3-7f60abb7d6a1
ms.openlocfilehash: 33c7367626d66d1db2705fc2882ca0780d1b867f
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/23/2020
ms.locfileid: "91090350"
---
# <a name="caller-information-visual-basic"></a>Informations relatives à l’appelant (Visual Basic)

À l'aide des attributs d'informations de l'appelant, vous pouvez obtenir des informations sur l'appelant d'une méthode. Vous pouvez obtenir le chemin d'accès du fichier de code source, le numéro de ligne dans le code source, puis le nom du membre de l'appelant. Ces informations sont utiles pour suivre, déboguer, et créer des outils de diagnostic.  
  
 Pour obtenir ces informations, vous utilisez les attributs qui sont appliqués aux paramètres facultatifs, qui a une valeur par défaut. Le tableau suivant répertorie les attributs d'informations de l'appelant définis dans l'espace de noms <xref:System.Runtime.CompilerServices?displayProperty=nameWithType> :  
  
|Attribut|Description|Type|  
|---|---|---|  
|<xref:System.Runtime.CompilerServices.CallerFilePathAttribute>|Chemin d’accès complet du fichier source qui contient l’appelant. C’est le chemin du fichier au moment de la compilation.|`String`|  
|<xref:System.Runtime.CompilerServices.CallerLineNumberAttribute>|Numéro de ligne dans le fichier source dans lequel la méthode est appelée.|`Integer`|  
|<xref:System.Runtime.CompilerServices.CallerMemberNameAttribute>|Méthode ou nom de la propriété de l'appelant. Consultez [Noms de membres](#MEMBERNAMES), plus loin dans cette rubrique.|`String`|  
  
## <a name="example"></a>Exemple  

 L'exemple suivant indique comment utiliser des attributs d'informations de l'appelant. À chaque appel à la méthode `TraceMessage`, les informations d'appel sont remplacées par des arguments pour les paramètres optionnels.  
  
```vb  
Private Sub DoProcessing()  
    TraceMessage("Something happened.")  
End Sub  
  
Public Sub TraceMessage(message As String,  
        <System.Runtime.CompilerServices.CallerMemberName> Optional memberName As String = Nothing,  
        <System.Runtime.CompilerServices.CallerFilePath> Optional sourcefilePath As String = Nothing,  
        <System.Runtime.CompilerServices.CallerLineNumber()> Optional sourceLineNumber As Integer = 0)  
  
    System.Diagnostics.Trace.WriteLine("message: " & message)  
    System.Diagnostics.Trace.WriteLine("member name: " & memberName)  
    System.Diagnostics.Trace.WriteLine("source file path: " & sourcefilePath)  
    System.Diagnostics.Trace.WriteLine("source line number: " & sourceLineNumber)  
End Sub  
  
' Sample output:  
'   message: Something happened.  
'   member name: DoProcessing  
'   source file path: C:\Users\username\Documents\Visual Studio 2012\Projects\CallerInfoVB\CallerInfoVB\Form1.vb  
'   source line number: 15  
```  
  
## <a name="remarks"></a>Notes  

 Vous devez spécifier une valeur par défaut explicite pour chaque paramètre optionnel. Vous ne pouvez pas appliquer des attributs d'informations de l'appelant aux paramètres qui ne sont pas spécifiés comme facultatifs.  
  
 Les attributs d'informations de l'appelant ne rendent pas un paramètre facultatif. À la place, ils affectent la valeur par défaut qui est passée si l'argument est oublié.  
  
 Les valeurs d'informations de l'appelant sont émises en tant que littéraux en langage intermédiaire (IL) au moment de la compilation. Contrairement aux résultats de la propriété <xref:System.Exception.StackTrace%2A> pour les exceptions, les résultats ne sont pas affectés par l'obfuscation (protection de code).  
  
 Vous pouvez fournir explicitement les arguments facultatifs pour contrôler ou masquer des informations de l'appelant.  
  
### <a name="member-names"></a><a name="MEMBERNAMES"></a> Noms de membres  

 Vous pouvez utiliser l'attribut `CallerMemberName` pour éviter de spécifier le nom du membre comme argument de `String` à la méthode appelée. Vous évitez ainsi le problème que la **refactorisation de changement de nom** ne modifie pas les valeurs `String`. Cet avantage est particulièrement utile pour les tâches suivantes :  
  
- Utilisation du traçage et des programmes de diagnostic.  
  
- Implémentation de l'interface <xref:System.ComponentModel.INotifyPropertyChanged> lors de la liaison de données. Cette interface permet à la propriété d'un objet de signaler à un contrôle dépendant que la propriété a été modifiée, afin que ce contrôle puisse afficher les informations mises à jour. Sans attribut `CallerMemberName`, vous devez spécifier le nom de la propriété comme littéral.  
  
 Le graphique suivant affiche les noms des membres qui sont retournés lorsque vous utilisez l'attribut `CallerMemberName`.  
  
|Les appels se produisent à l'intérieur|Résultat de nom de membre|  
|-------------------------|------------------------|  
|Méthode, propriété ou événement|Le nom de la méthode, la propriété ou l'événement dont l'appel est originaire.|  
|Constructeur|La chaîne « .ctor »|  
|Constructeur statique|La chaîne « .cctor »|  
|Destructeur|La chaîne « finalize »|  
|Opérateurs définis par l'utilisateur ou conversions|Le nom généré pour le membre, par exemple, « op_Addition ».|  
|Constructeur d'attribut|Le nom du membre auquel l'attribut est appliqué. Si l'attribut est un élément dans un membre (tel qu'un paramètre, une valeur de retour, ou un paramètre de type générique), le résultat est le nom du membre qui est associé à cet élément.|  
|Aucun membre contenant (par exemple, niveau assembly ou attributs qui sont appliqués aux types)|Valeur par défaut du paramètre optionnel.|  
  
## <a name="see-also"></a>Voir aussi

- [Attributs (Visual Basic)](../../language-reference/attributes.md)
- [Attributs courants (Visual Basic)](attributes/common-attributes.md)
- [Paramètres facultatifs](../language-features/procedures/optional-parameters.md)
- [Concepts de programmation (Visual Basic)](index.md)
