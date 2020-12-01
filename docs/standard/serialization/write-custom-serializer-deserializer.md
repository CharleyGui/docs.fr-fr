---
title: Comment écrire des sérialiseurs et des désérialiseurs personnalisés avec System.Text.Json
description: Découvrez comment écrire des sérialiseurs et des désérialiseurs personnalisés pour JSON, à l’aide de l' System.Text.Json espace de noms.
ms.date: 11/30/2020
no-loc:
- System.Text.Json
- Newtonsoft.Json
helpviewer_keywords:
- JSON serialization
- serializing objects
- serialization
- objects, serializing
ms.openlocfilehash: a01d3c8dd18c114ea1c3aabc402bc841a6025ffe
ms.sourcegitcommit: 721c3e4bdbb1ea0bb420818ec944c538fe5c513a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/01/2020
ms.locfileid: "96439992"
---
# <a name="how-to-write-custom-serializers-and-deserializers-with-no-locsystemtextjson"></a>Comment écrire des sérialiseurs et des désérialiseurs personnalisés avec System.Text.Json

<xref:System.Text.Json.Utf8JsonReader?displayProperty=fullName> est un lecteur haute performance, à faible allocation et en avant uniquement pour le texte JSON encodé en UTF-8, lu à partir d’un ou d’un `ReadOnlySpan<byte>` `ReadOnlySequence<byte>` . Le `Utf8JsonReader` est un type de bas niveau qui peut être utilisé pour créer des analyseurs et des désérialiseurs personnalisés. La <xref:System.Text.Json.JsonSerializer.Deserialize%2A?displayProperty=nameWithType> méthode utilise des `Utf8JsonReader` couvertures.

<xref:System.Text.Json.Utf8JsonWriter?displayProperty=fullName> est une méthode très performante pour écrire du texte JSON encodé en UTF-8 à partir de types .NET courants tels que `String` , `Int32` et `DateTime` . Le writer est un type de bas niveau qui peut être utilisé pour créer des sérialiseurs personnalisés. La <xref:System.Text.Json.JsonSerializer.Serialize%2A?displayProperty=nameWithType> méthode utilise des `Utf8JsonWriter` couvertures.

<xref:System.Text.Json.JsonDocument?displayProperty=fullName> offre la possibilité de générer un Document Object Model en lecture seule (DOM) à l’aide de `Utf8JsonReader` . Le DOM fournit un accès aléatoire aux données dans une charge utile JSON. Les éléments JSON qui composent la charge utile sont accessibles via le <xref:System.Text.Json.JsonElement> type. Le `JsonElement` type fournit des énumérateurs de tableau et d’objet, ainsi que des API pour convertir du texte JSON en types .net courants. `JsonDocument` expose une <xref:System.Text.Json.JsonDocument.RootElement> propriété.

Les sections suivantes montrent comment utiliser ces outils pour lire et écrire du code JSON.

## <a name="use-jsondocument-for-access-to-data"></a>Utiliser JsonDocument pour l’accès aux données

L’exemple suivant montre comment utiliser la <xref:System.Text.Json.JsonDocument> classe pour l’accès aléatoire aux données d’une chaîne JSON :

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/JsonDocumentDataAccess.cs" id="AverageGrades1":::

Le code précédent :

* Suppose que le JSON à analyser se trouve dans une chaîne nommée `jsonString` .
* Calcule une qualité moyenne pour les objets d’un `Students` tableau qui ont une `Grade` propriété.
* Affecte une catégorie par défaut de 70 pour les étudiants qui n’ont pas de qualité.
* Compte les élèves en incrémentant une `count` variable à chaque itération. Une alternative consiste à appeler <xref:System.Text.Json.JsonElement.GetArrayLength%2A> , comme illustré dans l’exemple suivant :

  :::code language="csharp" source="snippets/system-text-json-how-to/csharp/JsonDocumentDataAccess.cs" id="AverageGrades2":::

Voici un exemple du JSON traité par ce code :

:::code language="json" source="snippets/system-text-json-how-to/csharp/GradesPrettyPrint.json":::

## <a name="use-jsondocument-to-write-json"></a>Utiliser JsonDocument pour écrire du code JSON

L’exemple suivant montre comment écrire du code JSON à partir d’un <xref:System.Text.Json.JsonDocument> :

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/JsonDocumentWriteJson.cs" id="Serialize":::

Le code précédent :

* Lit un fichier JSON, charge les données dans un `JsonDocument` et écrit le format JSON (Pretty-imprimed) dans un fichier.
* Utilise <xref:System.Text.Json.JsonDocumentOptions> pour spécifier que les commentaires dans le JSON d’entrée sont autorisés mais ignorés.
* Lorsque vous avez terminé, appelle <xref:System.Text.Json.Utf8JsonWriter.Flush%2A> sur le writer. Une alternative consiste à laisser le writer auto-vide lorsqu’il est supprimé.

Voici un exemple d’entrée JSON à traiter par l’exemple de code :

:::code language="json" source="snippets/system-text-json-how-to/csharp/Grades.json":::

Le résultat est la sortie JSON imprimée suivante :

:::code language="json" source="snippets/system-text-json-how-to/csharp/GradesPrettyPrint.json":::

## <a name="use-utf8jsonwriter"></a>Utiliser Utf8JsonWriter

L’exemple suivant montre comment utiliser la <xref:System.Text.Json.Utf8JsonWriter> classe :

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/Utf8WriterToStream.cs" id="Serialize":::

## <a name="use-utf8jsonreader"></a>Utiliser Utf8JsonReader

L’exemple suivant montre comment utiliser la <xref:System.Text.Json.Utf8JsonReader> classe :

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/Utf8ReaderFromBytes.cs" id="Deserialize":::

Le code précédent suppose que la `jsonUtf8` variable est un tableau d’octets qui contient un JSON valide, encodé au format UTF-8.

### <a name="filter-data-using-utf8jsonreader"></a>Filtrer les données à l’aide de Utf8JsonReader

L’exemple suivant montre comment lire un fichier de façon synchrone et rechercher une valeur.

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/Utf8ReaderFromFile.cs":::

Pour obtenir une version asynchrone de cet exemple, consultez [.net Samples JSON Project](https://github.com/dotnet/samples/blob/18e31a5f1abd4f347bf96bfdc3e40e2cfb36e319/core/json/Program.cs).

Le code précédent :

* Suppose que le JSON contient un tableau d’objets et que chaque objet peut contenir une propriété « Name » de type chaîne.
* Compte les objets et les valeurs de propriété « nom » qui se terminent par « University ».
* Suppose que le fichier est encodé au format UTF-16 et le transcode en UTF-8. Un fichier encodé au format UTF-8 peut être lu directement dans un `ReadOnlySpan<byte>` , à l’aide du code suivant :

  ```csharp
  ReadOnlySpan<byte> jsonReadOnlySpan = File.ReadAllBytes(fileName);
  ```

  Si le fichier contient une marque d’ordre d’octet (BOM) UTF-8, supprimez-le avant de passer les octets au `Utf8JsonReader` , puisque le lecteur attend du texte. Dans le cas contraire, la marque d’octet est considérée comme JSON non valide et le lecteur lève une exception.

Voici un exemple JSON que le code précédent peut lire. Le message de synthèse obtenu est « 2 sur 4 ont des noms qui se terminent par «University » :

:::code language="json" source="snippets/system-text-json-how-to/csharp/Universities.json":::

### <a name="read-from-a-stream-using-utf8jsonreader"></a>Lire à partir d’un flux à l’aide de Utf8JsonReader

Lors de la lecture d’un fichier volumineux (un gigaoctet ou plus en taille, par exemple), vous pouvez éviter d’avoir à charger la totalité du fichier en mémoire en même temps. Pour ce scénario, vous pouvez utiliser un <xref:System.IO.FileStream> .

Lorsque vous utilisez le `Utf8JsonReader` pour lire un flux, les règles suivantes s’appliquent :

* La mémoire tampon contenant la charge utile JSON partielle doit être au moins aussi grande que le plus grand jeton JSON au sein de celle-ci afin que le lecteur puisse avancer la progression.
* La mémoire tampon doit être au moins aussi grande que la plus grande séquence d’espaces blancs dans le JSON.
* Le lecteur n’effectue pas le suivi des données qu’il a lues jusqu’à ce qu’il Lise complètement le suivant <xref:System.Text.Json.Utf8JsonReader.TokenType%2A> dans la charge utile JSON. Ainsi, lorsqu’il y a des octets restants dans la mémoire tampon, vous devez les transmettre à nouveau au lecteur. Vous pouvez utiliser <xref:System.Text.Json.Utf8JsonReader.BytesConsumed%2A> pour déterminer le nombre d’octets restants.

Le code suivant illustre comment lire à partir d’un flux. L’exemple montre un <xref:System.IO.MemoryStream> . Un code similaire fonctionne avec un <xref:System.IO.FileStream> , sauf lorsque `FileStream` contient une nomenclature UTF-8 au début. Dans ce cas, vous devez supprimer ces trois octets de la mémoire tampon avant de passer les octets restants à `Utf8JsonReader` . Dans le cas contraire, le lecteur lèvera une exception, puisque la nomenclature n’est pas considérée comme une partie valide du JSON.

L’exemple de code commence par une mémoire tampon de 4 Ko et double la taille de la mémoire tampon chaque fois qu’il détecte que la taille n’est pas assez grande pour contenir un jeton JSON complet, ce qui est nécessaire pour que le lecteur fasse progresser la progression sur la charge utile JSON. L’exemple JSON fourni dans l’extrait de code déclenche une augmentation de la taille de la mémoire tampon uniquement si vous définissez une très petite taille de mémoire tampon initiale, par exemple 10 octets. Si vous définissez la taille de la mémoire tampon initiale sur 10, les `Console.WriteLine` instructions illustrent la cause et l’effet de la taille de la mémoire tampon augmente. Au niveau de la taille de la mémoire tampon initiale de 4 Ko, la totalité de l’exemple JSON est affichée par chaque `Console.WriteLine` , et la taille de la mémoire tampon ne doit jamais être augmentée.

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/Utf8ReaderPartialRead.cs":::

L’exemple précédent n’affecte aucune limite à la taille maximale de la mémoire tampon. Si la taille du jeton est trop grande, le code peut échouer avec une <xref:System.OutOfMemoryException> exception. Cela peut se produire si le JSON contient un jeton d’une taille d’environ 1 Go, car le doublement de la taille de 1 Go donne une taille trop importante pour tenir dans une `int32` mémoire tampon.

## <a name="see-also"></a>Voir aussi

* [System.Text.Json vue](system-text-json-overview.md)
* [Comment personnaliser l’encodage de caractères](system-text-json-character-encoding.md)
* [Comment écrire des convertisseurs personnalisés pour la sérialisation JSON](system-text-json-converters-how-to.md)
* [System.Text.Json Référence d’API](xref:System.Text.Json)
