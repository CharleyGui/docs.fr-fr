---
title: Informations relatives à l’appelant (C#)
ms.date: 07/20/2015
ms.assetid: ffad3d24-2fb7-4641-9124-53b5bc91d339
ms.openlocfilehash: 4b2c34945b47db01b0e655f68f92e4dae7445c2c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "69595339"
---
# <a name="caller-information-c"></a>Informations relatives à l’appelant (C#)

À l'aide des attributs d'informations de l'appelant, vous pouvez obtenir des informations sur l'appelant d'une méthode. Vous pouvez obtenir le chemin d'accès du fichier de code source, le numéro de ligne dans le code source, puis le nom du membre de l'appelant. Ces informations sont utiles pour suivre, déboguer, et créer des outils de diagnostic.

Pour obtenir ces informations, vous utilisez les attributs qui sont appliqués aux paramètres facultatifs, qui a une valeur par défaut. Le tableau suivant répertorie les attributs d'informations de l'appelant définis dans l'espace de noms <xref:System.Runtime.CompilerServices?displayProperty=nameWithType> :

|Attribut|Description|Type|
|---|---|---|
|<xref:System.Runtime.CompilerServices.CallerFilePathAttribute>|Chemin d’accès complet du fichier source qui contient l’appelant. C’est le chemin du fichier au moment de la compilation.|`String`|
|<xref:System.Runtime.CompilerServices.CallerLineNumberAttribute>|Numéro de ligne dans le fichier source dans lequel la méthode est appelée.|`Integer`|
|<xref:System.Runtime.CompilerServices.CallerMemberNameAttribute>|Méthode ou nom de la propriété de l'appelant. Consultez [Noms de membres](#member-names), plus loin dans cette rubrique.|`String`|

## <a name="example"></a> Exemple

L'exemple suivant indique comment utiliser des attributs d'informations de l'appelant. À chaque appel à la méthode `TraceMessage`, les informations d'appel sont remplacées par des arguments pour les paramètres optionnels.

```csharp
public void DoProcessing()
{
    TraceMessage("Something happened.");
}

public void TraceMessage(string message,
        [System.Runtime.CompilerServices.CallerMemberName] string memberName = "",
        [System.Runtime.CompilerServices.CallerFilePath] string sourceFilePath = "",
        [System.Runtime.CompilerServices.CallerLineNumber] int sourceLineNumber = 0)
{
    System.Diagnostics.Trace.WriteLine("message: " + message);
    System.Diagnostics.Trace.WriteLine("member name: " + memberName);
    System.Diagnostics.Trace.WriteLine("source file path: " + sourceFilePath);
    System.Diagnostics.Trace.WriteLine("source line number: " + sourceLineNumber);
}

// Sample Output:
//  message: Something happened.
//  member name: DoProcessing
//  source file path: c:\Visual Studio Projects\CallerInfoCS\CallerInfoCS\Form1.cs
//  source line number: 31
```

## <a name="remarks"></a>Notes 

Vous devez spécifier une valeur par défaut explicite pour chaque paramètre optionnel. Vous ne pouvez pas appliquer des attributs d'informations de l'appelant aux paramètres qui ne sont pas spécifiés comme facultatifs.

Les attributs d'informations de l'appelant ne rendent pas un paramètre facultatif. À la place, ils affectent la valeur par défaut qui est passée si l'argument est oublié.

Les valeurs d'informations de l'appelant sont émises en tant que littéraux en langage intermédiaire (IL) au moment de la compilation. Contrairement aux résultats de la propriété <xref:System.Exception.StackTrace%2A> pour les exceptions, les résultats ne sont pas affectés par l'obfuscation (protection de code).

Vous pouvez fournir explicitement les arguments facultatifs pour contrôler ou masquer des informations de l'appelant.

### <a name="member-names"></a>Noms de membres

Vous pouvez utiliser l'attribut `CallerMemberName` pour éviter de spécifier le nom du membre comme argument de `String` à la méthode appelée. Vous évitez ainsi le problème que la **refactorisation de changement de nom** ne modifie pas les valeurs `String`. Cet avantage est particulièrement utile pour les tâches suivantes :

- Utilisation du traçage et des programmes de diagnostic.

- Implémentation de l'interface <xref:System.ComponentModel.INotifyPropertyChanged> lors de la liaison de données. Cette interface permet à la propriété d'un objet de signaler à un contrôle dépendant que la propriété a été modifiée, afin que ce contrôle puisse afficher les informations mises à jour. Sans attribut `CallerMemberName`, vous devez spécifier le nom de la propriété comme littéral.

Le graphique suivant affiche les noms des membres qui sont retournés lorsque vous utilisez l'attribut `CallerMemberName`.

|Les appels se produisent à l'intérieur|Résultat de nom de membre|
|-|-|
|Méthode, propriété ou événement|Le nom de la méthode, la propriété ou l'événement dont l'appel est originaire.|
|Constructeur|La chaîne « .ctor »|
|Constructeur statique|La chaîne « .cctor »|
|Destructeur|La chaîne « finalize »|
|Opérateurs définis par l'utilisateur ou conversions|Le nom généré pour le membre, par exemple, « op_Addition ».|
|Constructeur d'attribut|Le nom de la méthode ou de la propriété à laquelle s’applique l'attribut. Si l'attribut est un élément dans un membre (tel qu'un paramètre, une valeur de retour, ou un paramètre de type générique), le résultat est le nom du membre qui est associé à cet élément.|
|Aucun membre contenant (par exemple, niveau assembly ou attributs qui sont appliqués aux types)|Valeur par défaut du paramètre optionnel.|

## <a name="see-also"></a>Voir aussi

- [Attributs (C#)](./attributes/index.md)
- [Attributs courants (C#)](./attributes/common-attributes.md)
- [Arguments nommés et facultatifs](../classes-and-structs/named-and-optional-arguments.md)
- [Concepts de programmation (C#)](./index.md)
