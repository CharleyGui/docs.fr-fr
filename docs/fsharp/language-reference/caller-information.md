---
title: Informations relatives à l’appelant
description: Décrit comment utiliser les attributs d’argument d’informations de l’appelant pour obtenir des informations d’appelant à partir d’une méthode.
ms.date: 11/04/2019
ms.openlocfilehash: 700cde26fbe4e6c48155f88bfc63af59af86cfe2
ms.sourcegitcommit: ecd9e9bb2225eb76f819722ea8b24988fe46f34c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/05/2020
ms.locfileid: "96739774"
---
# <a name="caller-information"></a>Informations relatives à l’appelant

À l'aide des attributs d'informations de l'appelant, vous pouvez obtenir des informations sur l'appelant d'une méthode. Vous pouvez obtenir le chemin d'accès du fichier de code source, le numéro de ligne dans le code source, puis le nom du membre de l'appelant. Ces informations sont utiles pour suivre, déboguer, et créer des outils de diagnostic.

Pour obtenir ces informations, vous utilisez les attributs qui sont appliqués aux paramètres facultatifs, qui a une valeur par défaut. Le tableau suivant répertorie les attributs d’informations de l’appelant qui sont définis dans l’espace de noms [System. Runtime. CompilerServices](/dotnet/api/system.runtime.compilerservices) :

|Attribut|Description|Type|
|---------|-----------|----|
|[CallerFilePath](/dotnet/api/system.runtime.compilerservices.callerfilepathattribute)|Chemin d’accès complet du fichier source qui contient l’appelant. C’est le chemin du fichier au moment de la compilation.|`String`
|[CallerLineNumber](/dotnet/api/system.runtime.compilerservices.callerlinenumberattribute)|Numéro de ligne dans le fichier source dans lequel la méthode est appelée.|`Integer`|
|[CallerMemberName](/dotnet/api/system.runtime.compilerservices.callermembernameattribute)|Méthode ou nom de la propriété de l'appelant. Consultez la section noms de membres plus loin dans cette rubrique.|`String`|

## <a name="example"></a>Exemple

L’exemple suivant montre comment vous pouvez utiliser ces attributs pour suivre un appelant.

```fsharp
open System.Diagnostics
open System.Runtime.CompilerServices
open System.Runtime.InteropServices

type Tracer() =
    member _.DoTrace(message: string,
                      [<CallerMemberName; Optional; DefaultParameterValue("")>] memberName: string,
                      [<CallerFilePath; Optional; DefaultParameterValue("")>] path: string,
                      [<CallerLineNumber; Optional; DefaultParameterValue(0)>] line: int) =
        Trace.WriteLine(sprintf $"Message: {message}")
        Trace.WriteLine(sprintf $"Member name: {memberName}")
        Trace.WriteLine(sprintf $"Source file path: {path}")
        Trace.WriteLine(sprintf $"Source line number: {line}")
```

## <a name="remarks"></a>Remarques

Les attributs d’informations de l’appelant ne peuvent être appliqués qu’à des paramètres facultatifs. Les attributs d’informations de l’appelant forcent le compilateur à écrire la valeur appropriée pour chaque paramètre facultatif décoré avec un attribut d’informations de l’appelant.

Les valeurs d'informations de l'appelant sont émises en tant que littéraux en langage intermédiaire (IL) au moment de la compilation. Contrairement aux résultats de la propriété [StackTrace](/dotnet/api/system.diagnostics.stacktrace) pour les exceptions, les résultats ne sont pas affectés par l’obscurcissement.

Vous pouvez fournir explicitement les arguments facultatifs pour contrôler ou masquer des informations de l'appelant.

## <a name="member-names"></a>Noms de membres

Vous pouvez utiliser l' [`CallerMemberName`](/dotnet/api/system.runtime.compilerservices.callermembernameattribute) attribut pour éviter de spécifier le nom de membre en tant qu' `String` argument de la méthode appelée. Vous évitez ainsi le problème que la refactorisation de changement de nom ne modifie pas les valeurs `String`. Cet avantage est particulièrement utile pour les tâches suivantes :

- Utilisation du traçage et des programmes de diagnostic.
- Implémentation de l’interface [INotifyPropertyChanged](/dotnet/api/system.componentmodel.inotifypropertychanged) lors de la liaison de données. Cette interface permet à la propriété d'un objet de signaler à un contrôle dépendant que la propriété a été modifiée, afin que ce contrôle puisse afficher les informations mises à jour. Sans l' [`CallerMemberName`](/dotnet/api/system.runtime.compilerservices.callermembernameattribute) attribut, vous devez spécifier le nom de la propriété en tant que littéral.

Le graphique suivant montre les noms de membres qui sont retournés lorsque vous utilisez l’attribut CallerMemberName.

|Les appels se produisent à l'intérieur|Résultat de nom de membre|
|-------------------|------------------|
|Méthode, propriété ou événement|Le nom de la méthode, la propriété ou l'événement dont l'appel est originaire.|
|Constructeur|La chaîne « .ctor »|
|Constructeur statique|La chaîne « .cctor »|
|Destructeur|La chaîne « finalize »|
|Opérateurs définis par l'utilisateur ou conversions|Le nom généré pour le membre, par exemple, « op_Addition ».|
|Constructeur d'attribut|Le nom du membre auquel l'attribut est appliqué. Si l'attribut est un élément dans un membre (tel qu'un paramètre, une valeur de retour, ou un paramètre de type générique), le résultat est le nom du membre qui est associé à cet élément.|
|Aucun membre contenant (par exemple, niveau assembly ou attributs qui sont appliqués aux types)|Valeur par défaut du paramètre optionnel.|

## <a name="see-also"></a>Voir aussi

- [Attributs](attributes.md)
- [Arguments nommés](parameters-and-arguments.md#named-arguments)
- [Paramètres facultatifs](parameters-and-arguments.md#optional-parameters)
