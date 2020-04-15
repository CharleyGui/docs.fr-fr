---
title: 'Attributs réservés C : Suivi des informations sur les appelants'
ms.date: 04/09/2020
description: Ces attributs instruisent le compilateur de générer des informations sur le code qui appelle un membre. Vous utilisez le CallerFilePath, CallerLineNumber et CallerMemberName pour fournir des informations détaillées sur les traces
ms.openlocfilehash: ee061d4cae35bdcc0b89007e360e94fee8c5f87c
ms.sourcegitcommit: c91110ef6ee3fedb591f3d628dc17739c4a7071e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/15/2020
ms.locfileid: "81389876"
---
# <a name="reserved-attributes-determine-caller-information"></a>Attributs réservés : Déterminer les informations sur l’appelant

En utilisant des attributs d’information, vous obtenez des informations sur l’appelant à une méthode. Vous obtenez le chemin de fichier du code source, le numéro de ligne dans le code source et le nom du membre de l’appelant. Pour obtenir des informations de membre de l’appelant, vous utilisez les attributs qui sont appliqués aux paramètres facultatifs. Chaque paramètre facultatif spécifie une valeur par défaut. Le tableau suivant répertorie les attributs d'informations de l'appelant définis dans l'espace de noms <xref:System.Runtime.CompilerServices?displayProperty=nameWithType> :

|Attribut|Description|Type|
|---|---|---|
|<xref:System.Runtime.CompilerServices.CallerFilePathAttribute>|Chemin d’accès complet du fichier source qui contient l’appelant. Le chemin complet est le chemin au moment de la compilation.|`String`|
|<xref:System.Runtime.CompilerServices.CallerLineNumberAttribute>|Numéro de ligne dans le fichier source à partir duquel la méthode est appelée.|`Integer`|
|<xref:System.Runtime.CompilerServices.CallerMemberNameAttribute>|Nom de la méthode ou nom de la propriété de l’appelant.|`String`|

Ces informations vous aident à écrire des traçages, à débogage et à créer des outils de diagnostic. L’exemple suivant montre comment utiliser les attributs d’info de l’appelant. À chaque appel à la méthode `TraceMessage`, les informations d'appel sont remplacées par des arguments pour les paramètres optionnels.

```csharp
public void DoProcessing()
{
    TraceMessage("Something happened.");
}

public void TraceMessage(string message,
        [CallerMemberName] string memberName = "",
        [CallerFilePath] string sourceFilePath = "",
        [CallerLineNumber] int sourceLineNumber = 0)
{
    Trace.WriteLine("message: " + message);
    Trace.WriteLine("member name: " + memberName);
    Trace.WriteLine("source file path: " + sourceFilePath);
    Trace.WriteLine("source line number: " + sourceLineNumber);
}

// Sample Output:
//  message: Something happened.
//  member name: DoProcessing
//  source file path: c:\Visual Studio Projects\CallerInfoCS\CallerInfoCS\Form1.cs
//  source line number: 31
```

Vous spécifiez une valeur par défaut explicite pour chaque paramètre facultatif. Vous ne pouvez pas appliquer des attributs d’information de l’appelant à des paramètres qui ne sont pas spécifiés comme facultatifs. Les attributs d’info de l’appelant ne rendent pas un paramètre facultatif. À la place, ils affectent la valeur par défaut qui est passée si l'argument est oublié. Les valeurs d’info de l’appelant sont émises sous forme d’alphabétisés dans la langue intermédiaire (IL) au moment de la compilation. Contrairement aux résultats de la propriété <xref:System.Exception.StackTrace%2A> pour les exceptions, les résultats ne sont pas affectés par l'obfuscation (protection de code). Vous pouvez fournir explicitement les arguments facultatifs pour contrôler ou masquer des informations de l'appelant.

### <a name="member-names"></a>Noms de membres

Vous pouvez utiliser l'attribut `CallerMemberName` pour éviter de spécifier le nom du membre comme argument de `String` à la méthode appelée. Vous évitez ainsi le problème que la **refactorisation de changement de nom** ne modifie pas les valeurs `String`. Cet avantage est particulièrement utile pour les tâches suivantes :

- Utilisation du traçage et des programmes de diagnostic.
- Implémentation de l'interface <xref:System.ComponentModel.INotifyPropertyChanged> lors de la liaison de données. Cette interface permet à la propriété d'un objet de signaler à un contrôle dépendant que la propriété a été modifiée, afin que ce contrôle puisse afficher les informations mises à jour. Sans attribut `CallerMemberName`, vous devez spécifier le nom de la propriété comme littéral.

Le graphique suivant affiche les noms des membres qui sont retournés lorsque vous utilisez l'attribut `CallerMemberName`.

|Les appels se produisent à l’intérieur|Résultat de nom de membre|
|-|-|
|Méthode, propriété ou événement|Le nom de la méthode, la propriété ou l'événement dont l'appel est originaire.|
|Constructeur|La chaîne « .ctor »|
|Constructeur statique|La chaîne « .cctor »|
|Destructeur|La chaîne « finalize »|
|Opérateurs définis par l'utilisateur ou conversions|Le nom généré pour le membre, par exemple, « op_Addition ».|
|Constructeur d'attribut|Le nom de la méthode ou de la propriété à laquelle s’applique l'attribut. Si l'attribut est un élément dans un membre (tel qu'un paramètre, une valeur de retour, ou un paramètre de type générique), le résultat est le nom du membre qui est associé à cet élément.|
|Aucun membre contenant (par exemple, niveau assembly ou attributs qui sont appliqués aux types)|Valeur par défaut du paramètre optionnel.|

## <a name="see-also"></a>Voir aussi

- [Arguments nommés et facultatifs](../../programming-guide/classes-and-structs/named-and-optional-arguments.md)
- <xref:System.Reflection>
- <xref:System.Attribute>
- [Attributs](../../../standard/attributes/index.md)
