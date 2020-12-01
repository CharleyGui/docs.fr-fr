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
# <a name="how-to-write-custom-serializers-and-deserializers-with-no-locsystemtextjson"></a><span data-ttu-id="55baa-103">Comment écrire des sérialiseurs et des désérialiseurs personnalisés avec System.Text.Json</span><span class="sxs-lookup"><span data-stu-id="55baa-103">How to write custom serializers and deserializers with System.Text.Json</span></span>

<span data-ttu-id="55baa-104"><xref:System.Text.Json.Utf8JsonReader?displayProperty=fullName> est un lecteur haute performance, à faible allocation et en avant uniquement pour le texte JSON encodé en UTF-8, lu à partir d’un ou d’un `ReadOnlySpan<byte>` `ReadOnlySequence<byte>` .</span><span class="sxs-lookup"><span data-stu-id="55baa-104"><xref:System.Text.Json.Utf8JsonReader?displayProperty=fullName> is a high-performance, low allocation, forward-only reader for UTF-8 encoded JSON text, read from a `ReadOnlySpan<byte>` or `ReadOnlySequence<byte>`.</span></span> <span data-ttu-id="55baa-105">Le `Utf8JsonReader` est un type de bas niveau qui peut être utilisé pour créer des analyseurs et des désérialiseurs personnalisés.</span><span class="sxs-lookup"><span data-stu-id="55baa-105">The `Utf8JsonReader` is a low-level type that can be used to build custom parsers and deserializers.</span></span> <span data-ttu-id="55baa-106">La <xref:System.Text.Json.JsonSerializer.Deserialize%2A?displayProperty=nameWithType> méthode utilise des `Utf8JsonReader` couvertures.</span><span class="sxs-lookup"><span data-stu-id="55baa-106">The <xref:System.Text.Json.JsonSerializer.Deserialize%2A?displayProperty=nameWithType> method uses `Utf8JsonReader` under the covers.</span></span>

<span data-ttu-id="55baa-107"><xref:System.Text.Json.Utf8JsonWriter?displayProperty=fullName> est une méthode très performante pour écrire du texte JSON encodé en UTF-8 à partir de types .NET courants tels que `String` , `Int32` et `DateTime` .</span><span class="sxs-lookup"><span data-stu-id="55baa-107"><xref:System.Text.Json.Utf8JsonWriter?displayProperty=fullName> is a high-performance way to write UTF-8 encoded JSON text from common .NET types like `String`, `Int32`, and `DateTime`.</span></span> <span data-ttu-id="55baa-108">Le writer est un type de bas niveau qui peut être utilisé pour créer des sérialiseurs personnalisés.</span><span class="sxs-lookup"><span data-stu-id="55baa-108">The writer is a low-level type that can be used to build custom serializers.</span></span> <span data-ttu-id="55baa-109">La <xref:System.Text.Json.JsonSerializer.Serialize%2A?displayProperty=nameWithType> méthode utilise des `Utf8JsonWriter` couvertures.</span><span class="sxs-lookup"><span data-stu-id="55baa-109">The <xref:System.Text.Json.JsonSerializer.Serialize%2A?displayProperty=nameWithType> method uses `Utf8JsonWriter` under the covers.</span></span>

<span data-ttu-id="55baa-110"><xref:System.Text.Json.JsonDocument?displayProperty=fullName> offre la possibilité de générer un Document Object Model en lecture seule (DOM) à l’aide de `Utf8JsonReader` .</span><span class="sxs-lookup"><span data-stu-id="55baa-110"><xref:System.Text.Json.JsonDocument?displayProperty=fullName> provides the ability to build a read-only Document Object Model (DOM) by using `Utf8JsonReader`.</span></span> <span data-ttu-id="55baa-111">Le DOM fournit un accès aléatoire aux données dans une charge utile JSON.</span><span class="sxs-lookup"><span data-stu-id="55baa-111">The DOM provides random access to data in a JSON payload.</span></span> <span data-ttu-id="55baa-112">Les éléments JSON qui composent la charge utile sont accessibles via le <xref:System.Text.Json.JsonElement> type.</span><span class="sxs-lookup"><span data-stu-id="55baa-112">The JSON elements that compose the payload can be accessed via the <xref:System.Text.Json.JsonElement> type.</span></span> <span data-ttu-id="55baa-113">Le `JsonElement` type fournit des énumérateurs de tableau et d’objet, ainsi que des API pour convertir du texte JSON en types .net courants.</span><span class="sxs-lookup"><span data-stu-id="55baa-113">The `JsonElement` type provides array and object enumerators along with APIs to convert JSON text to common .NET types.</span></span> <span data-ttu-id="55baa-114">`JsonDocument` expose une <xref:System.Text.Json.JsonDocument.RootElement> propriété.</span><span class="sxs-lookup"><span data-stu-id="55baa-114">`JsonDocument` exposes a <xref:System.Text.Json.JsonDocument.RootElement> property.</span></span>

<span data-ttu-id="55baa-115">Les sections suivantes montrent comment utiliser ces outils pour lire et écrire du code JSON.</span><span class="sxs-lookup"><span data-stu-id="55baa-115">The following sections show how to use these tools for reading and writing JSON.</span></span>

## <a name="use-jsondocument-for-access-to-data"></a><span data-ttu-id="55baa-116">Utiliser JsonDocument pour l’accès aux données</span><span class="sxs-lookup"><span data-stu-id="55baa-116">Use JsonDocument for access to data</span></span>

<span data-ttu-id="55baa-117">L’exemple suivant montre comment utiliser la <xref:System.Text.Json.JsonDocument> classe pour l’accès aléatoire aux données d’une chaîne JSON :</span><span class="sxs-lookup"><span data-stu-id="55baa-117">The following example shows how to use the <xref:System.Text.Json.JsonDocument> class for random access to data in a JSON string:</span></span>

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/JsonDocumentDataAccess.cs" id="AverageGrades1":::

<span data-ttu-id="55baa-118">Le code précédent :</span><span class="sxs-lookup"><span data-stu-id="55baa-118">The preceding code:</span></span>

* <span data-ttu-id="55baa-119">Suppose que le JSON à analyser se trouve dans une chaîne nommée `jsonString` .</span><span class="sxs-lookup"><span data-stu-id="55baa-119">Assumes the JSON to analyze is in a string named `jsonString`.</span></span>
* <span data-ttu-id="55baa-120">Calcule une qualité moyenne pour les objets d’un `Students` tableau qui ont une `Grade` propriété.</span><span class="sxs-lookup"><span data-stu-id="55baa-120">Calculates an average grade for objects in a `Students` array that have a `Grade` property.</span></span>
* <span data-ttu-id="55baa-121">Affecte une catégorie par défaut de 70 pour les étudiants qui n’ont pas de qualité.</span><span class="sxs-lookup"><span data-stu-id="55baa-121">Assigns a default grade of 70 for students who don't have a grade.</span></span>
* <span data-ttu-id="55baa-122">Compte les élèves en incrémentant une `count` variable à chaque itération.</span><span class="sxs-lookup"><span data-stu-id="55baa-122">Counts students by incrementing a `count` variable with each iteration.</span></span> <span data-ttu-id="55baa-123">Une alternative consiste à appeler <xref:System.Text.Json.JsonElement.GetArrayLength%2A> , comme illustré dans l’exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="55baa-123">An alternative is to call <xref:System.Text.Json.JsonElement.GetArrayLength%2A>, as shown in the following example:</span></span>

  :::code language="csharp" source="snippets/system-text-json-how-to/csharp/JsonDocumentDataAccess.cs" id="AverageGrades2":::

<span data-ttu-id="55baa-124">Voici un exemple du JSON traité par ce code :</span><span class="sxs-lookup"><span data-stu-id="55baa-124">Here's an example of the JSON that this code processes:</span></span>

:::code language="json" source="snippets/system-text-json-how-to/csharp/GradesPrettyPrint.json":::

## <a name="use-jsondocument-to-write-json"></a><span data-ttu-id="55baa-125">Utiliser JsonDocument pour écrire du code JSON</span><span class="sxs-lookup"><span data-stu-id="55baa-125">Use JsonDocument to write JSON</span></span>

<span data-ttu-id="55baa-126">L’exemple suivant montre comment écrire du code JSON à partir d’un <xref:System.Text.Json.JsonDocument> :</span><span class="sxs-lookup"><span data-stu-id="55baa-126">The following example shows how to write JSON from a <xref:System.Text.Json.JsonDocument>:</span></span>

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/JsonDocumentWriteJson.cs" id="Serialize":::

<span data-ttu-id="55baa-127">Le code précédent :</span><span class="sxs-lookup"><span data-stu-id="55baa-127">The preceding code:</span></span>

* <span data-ttu-id="55baa-128">Lit un fichier JSON, charge les données dans un `JsonDocument` et écrit le format JSON (Pretty-imprimed) dans un fichier.</span><span class="sxs-lookup"><span data-stu-id="55baa-128">Reads a JSON file, loads the data into a `JsonDocument`, and writes formatted (pretty-printed) JSON to a file.</span></span>
* <span data-ttu-id="55baa-129">Utilise <xref:System.Text.Json.JsonDocumentOptions> pour spécifier que les commentaires dans le JSON d’entrée sont autorisés mais ignorés.</span><span class="sxs-lookup"><span data-stu-id="55baa-129">Uses <xref:System.Text.Json.JsonDocumentOptions> to specify that comments in the input JSON are allowed but ignored.</span></span>
* <span data-ttu-id="55baa-130">Lorsque vous avez terminé, appelle <xref:System.Text.Json.Utf8JsonWriter.Flush%2A> sur le writer.</span><span class="sxs-lookup"><span data-stu-id="55baa-130">When finished, calls <xref:System.Text.Json.Utf8JsonWriter.Flush%2A> on the writer.</span></span> <span data-ttu-id="55baa-131">Une alternative consiste à laisser le writer auto-vide lorsqu’il est supprimé.</span><span class="sxs-lookup"><span data-stu-id="55baa-131">An alternative is to let the writer auto-flush when it's disposed.</span></span>

<span data-ttu-id="55baa-132">Voici un exemple d’entrée JSON à traiter par l’exemple de code :</span><span class="sxs-lookup"><span data-stu-id="55baa-132">Here's an example of JSON input to be processed by the example code:</span></span>

:::code language="json" source="snippets/system-text-json-how-to/csharp/Grades.json":::

<span data-ttu-id="55baa-133">Le résultat est la sortie JSON imprimée suivante :</span><span class="sxs-lookup"><span data-stu-id="55baa-133">The result is the following pretty-printed JSON output:</span></span>

:::code language="json" source="snippets/system-text-json-how-to/csharp/GradesPrettyPrint.json":::

## <a name="use-utf8jsonwriter"></a><span data-ttu-id="55baa-134">Utiliser Utf8JsonWriter</span><span class="sxs-lookup"><span data-stu-id="55baa-134">Use Utf8JsonWriter</span></span>

<span data-ttu-id="55baa-135">L’exemple suivant montre comment utiliser la <xref:System.Text.Json.Utf8JsonWriter> classe :</span><span class="sxs-lookup"><span data-stu-id="55baa-135">The following example shows how to use the <xref:System.Text.Json.Utf8JsonWriter> class:</span></span>

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/Utf8WriterToStream.cs" id="Serialize":::

## <a name="use-utf8jsonreader"></a><span data-ttu-id="55baa-136">Utiliser Utf8JsonReader</span><span class="sxs-lookup"><span data-stu-id="55baa-136">Use Utf8JsonReader</span></span>

<span data-ttu-id="55baa-137">L’exemple suivant montre comment utiliser la <xref:System.Text.Json.Utf8JsonReader> classe :</span><span class="sxs-lookup"><span data-stu-id="55baa-137">The following example shows how to use the <xref:System.Text.Json.Utf8JsonReader> class:</span></span>

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/Utf8ReaderFromBytes.cs" id="Deserialize":::

<span data-ttu-id="55baa-138">Le code précédent suppose que la `jsonUtf8` variable est un tableau d’octets qui contient un JSON valide, encodé au format UTF-8.</span><span class="sxs-lookup"><span data-stu-id="55baa-138">The preceding code assumes that the `jsonUtf8` variable is a byte array that contains valid JSON, encoded as UTF-8.</span></span>

### <a name="filter-data-using-utf8jsonreader"></a><span data-ttu-id="55baa-139">Filtrer les données à l’aide de Utf8JsonReader</span><span class="sxs-lookup"><span data-stu-id="55baa-139">Filter data using Utf8JsonReader</span></span>

<span data-ttu-id="55baa-140">L’exemple suivant montre comment lire un fichier de façon synchrone et rechercher une valeur.</span><span class="sxs-lookup"><span data-stu-id="55baa-140">The following example shows how to synchronously read a file, and search for a value.</span></span>

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/Utf8ReaderFromFile.cs":::

<span data-ttu-id="55baa-141">Pour obtenir une version asynchrone de cet exemple, consultez [.net Samples JSON Project](https://github.com/dotnet/samples/blob/18e31a5f1abd4f347bf96bfdc3e40e2cfb36e319/core/json/Program.cs).</span><span class="sxs-lookup"><span data-stu-id="55baa-141">For an asynchronous version of this example, see [.NET samples JSON project](https://github.com/dotnet/samples/blob/18e31a5f1abd4f347bf96bfdc3e40e2cfb36e319/core/json/Program.cs).</span></span>

<span data-ttu-id="55baa-142">Le code précédent :</span><span class="sxs-lookup"><span data-stu-id="55baa-142">The preceding code:</span></span>

* <span data-ttu-id="55baa-143">Suppose que le JSON contient un tableau d’objets et que chaque objet peut contenir une propriété « Name » de type chaîne.</span><span class="sxs-lookup"><span data-stu-id="55baa-143">Assumes the JSON contains an array of objects and each object may contain a "name" property of type string.</span></span>
* <span data-ttu-id="55baa-144">Compte les objets et les valeurs de propriété « nom » qui se terminent par « University ».</span><span class="sxs-lookup"><span data-stu-id="55baa-144">Counts objects and "name" property values that end with "University".</span></span>
* <span data-ttu-id="55baa-145">Suppose que le fichier est encodé au format UTF-16 et le transcode en UTF-8.</span><span class="sxs-lookup"><span data-stu-id="55baa-145">Assumes the file is encoded as UTF-16 and transcodes it into UTF-8.</span></span> <span data-ttu-id="55baa-146">Un fichier encodé au format UTF-8 peut être lu directement dans un `ReadOnlySpan<byte>` , à l’aide du code suivant :</span><span class="sxs-lookup"><span data-stu-id="55baa-146">A file encoded as UTF-8 can be read directly into a `ReadOnlySpan<byte>`, by using the following code:</span></span>

  ```csharp
  ReadOnlySpan<byte> jsonReadOnlySpan = File.ReadAllBytes(fileName);
  ```

  <span data-ttu-id="55baa-147">Si le fichier contient une marque d’ordre d’octet (BOM) UTF-8, supprimez-le avant de passer les octets au `Utf8JsonReader` , puisque le lecteur attend du texte.</span><span class="sxs-lookup"><span data-stu-id="55baa-147">If the file contains a UTF-8 byte order mark (BOM), remove it before passing the bytes to the `Utf8JsonReader`, since the reader expects text.</span></span> <span data-ttu-id="55baa-148">Dans le cas contraire, la marque d’octet est considérée comme JSON non valide et le lecteur lève une exception.</span><span class="sxs-lookup"><span data-stu-id="55baa-148">Otherwise, the BOM is considered invalid JSON, and the reader throws an exception.</span></span>

<span data-ttu-id="55baa-149">Voici un exemple JSON que le code précédent peut lire.</span><span class="sxs-lookup"><span data-stu-id="55baa-149">Here's a JSON sample that the preceding code can read.</span></span> <span data-ttu-id="55baa-150">Le message de synthèse obtenu est « 2 sur 4 ont des noms qui se terminent par «University » :</span><span class="sxs-lookup"><span data-stu-id="55baa-150">The resulting summary message is "2 out of 4 have names that end with 'University'":</span></span>

:::code language="json" source="snippets/system-text-json-how-to/csharp/Universities.json":::

### <a name="read-from-a-stream-using-utf8jsonreader"></a><span data-ttu-id="55baa-151">Lire à partir d’un flux à l’aide de Utf8JsonReader</span><span class="sxs-lookup"><span data-stu-id="55baa-151">Read from a stream using Utf8JsonReader</span></span>

<span data-ttu-id="55baa-152">Lors de la lecture d’un fichier volumineux (un gigaoctet ou plus en taille, par exemple), vous pouvez éviter d’avoir à charger la totalité du fichier en mémoire en même temps.</span><span class="sxs-lookup"><span data-stu-id="55baa-152">When reading a large file (a gigabyte or more in size, for example), you might want to avoid having to load the entire file into memory at once.</span></span> <span data-ttu-id="55baa-153">Pour ce scénario, vous pouvez utiliser un <xref:System.IO.FileStream> .</span><span class="sxs-lookup"><span data-stu-id="55baa-153">For this scenario, you can use a <xref:System.IO.FileStream>.</span></span>

<span data-ttu-id="55baa-154">Lorsque vous utilisez le `Utf8JsonReader` pour lire un flux, les règles suivantes s’appliquent :</span><span class="sxs-lookup"><span data-stu-id="55baa-154">When using the `Utf8JsonReader` to read from a stream, the following rules apply:</span></span>

* <span data-ttu-id="55baa-155">La mémoire tampon contenant la charge utile JSON partielle doit être au moins aussi grande que le plus grand jeton JSON au sein de celle-ci afin que le lecteur puisse avancer la progression.</span><span class="sxs-lookup"><span data-stu-id="55baa-155">The buffer containing the partial JSON payload must be at least as large as the largest JSON token within it so that the reader can make forward progress.</span></span>
* <span data-ttu-id="55baa-156">La mémoire tampon doit être au moins aussi grande que la plus grande séquence d’espaces blancs dans le JSON.</span><span class="sxs-lookup"><span data-stu-id="55baa-156">The buffer must be at least as large as the largest sequence of white space within the JSON.</span></span>
* <span data-ttu-id="55baa-157">Le lecteur n’effectue pas le suivi des données qu’il a lues jusqu’à ce qu’il Lise complètement le suivant <xref:System.Text.Json.Utf8JsonReader.TokenType%2A> dans la charge utile JSON.</span><span class="sxs-lookup"><span data-stu-id="55baa-157">The reader doesn't keep track of the data it has read until it completely reads the next <xref:System.Text.Json.Utf8JsonReader.TokenType%2A> in the JSON payload.</span></span> <span data-ttu-id="55baa-158">Ainsi, lorsqu’il y a des octets restants dans la mémoire tampon, vous devez les transmettre à nouveau au lecteur.</span><span class="sxs-lookup"><span data-stu-id="55baa-158">So when there are bytes left over in the buffer, you have to pass them to the reader again.</span></span> <span data-ttu-id="55baa-159">Vous pouvez utiliser <xref:System.Text.Json.Utf8JsonReader.BytesConsumed%2A> pour déterminer le nombre d’octets restants.</span><span class="sxs-lookup"><span data-stu-id="55baa-159">You can use <xref:System.Text.Json.Utf8JsonReader.BytesConsumed%2A> to determine how many bytes are left over.</span></span>

<span data-ttu-id="55baa-160">Le code suivant illustre comment lire à partir d’un flux.</span><span class="sxs-lookup"><span data-stu-id="55baa-160">The following code illustrates how to read from a stream.</span></span> <span data-ttu-id="55baa-161">L’exemple montre un <xref:System.IO.MemoryStream> .</span><span class="sxs-lookup"><span data-stu-id="55baa-161">The example shows a <xref:System.IO.MemoryStream>.</span></span> <span data-ttu-id="55baa-162">Un code similaire fonctionne avec un <xref:System.IO.FileStream> , sauf lorsque `FileStream` contient une nomenclature UTF-8 au début.</span><span class="sxs-lookup"><span data-stu-id="55baa-162">Similar code will work with a <xref:System.IO.FileStream>, except when the `FileStream` contains a UTF-8 BOM at the start.</span></span> <span data-ttu-id="55baa-163">Dans ce cas, vous devez supprimer ces trois octets de la mémoire tampon avant de passer les octets restants à `Utf8JsonReader` .</span><span class="sxs-lookup"><span data-stu-id="55baa-163">In that case, you need to strip those three bytes from the buffer before passing the remaining bytes to the `Utf8JsonReader`.</span></span> <span data-ttu-id="55baa-164">Dans le cas contraire, le lecteur lèvera une exception, puisque la nomenclature n’est pas considérée comme une partie valide du JSON.</span><span class="sxs-lookup"><span data-stu-id="55baa-164">Otherwise the reader would throw an exception, since the BOM is not considered a valid part of the JSON.</span></span>

<span data-ttu-id="55baa-165">L’exemple de code commence par une mémoire tampon de 4 Ko et double la taille de la mémoire tampon chaque fois qu’il détecte que la taille n’est pas assez grande pour contenir un jeton JSON complet, ce qui est nécessaire pour que le lecteur fasse progresser la progression sur la charge utile JSON.</span><span class="sxs-lookup"><span data-stu-id="55baa-165">The sample code starts with a 4KB buffer and doubles the buffer size each time it finds that the size is not large enough to fit a complete JSON token, which is required for the reader to make forward progress on the JSON payload.</span></span> <span data-ttu-id="55baa-166">L’exemple JSON fourni dans l’extrait de code déclenche une augmentation de la taille de la mémoire tampon uniquement si vous définissez une très petite taille de mémoire tampon initiale, par exemple 10 octets.</span><span class="sxs-lookup"><span data-stu-id="55baa-166">The JSON sample provided in the snippet triggers a buffer size increase only if you set a very small initial buffer size, for example, 10 bytes.</span></span> <span data-ttu-id="55baa-167">Si vous définissez la taille de la mémoire tampon initiale sur 10, les `Console.WriteLine` instructions illustrent la cause et l’effet de la taille de la mémoire tampon augmente.</span><span class="sxs-lookup"><span data-stu-id="55baa-167">If you set the initial buffer size to 10, the `Console.WriteLine` statements illustrate the cause and effect of buffer size increases.</span></span> <span data-ttu-id="55baa-168">Au niveau de la taille de la mémoire tampon initiale de 4 Ko, la totalité de l’exemple JSON est affichée par chaque `Console.WriteLine` , et la taille de la mémoire tampon ne doit jamais être augmentée.</span><span class="sxs-lookup"><span data-stu-id="55baa-168">At the 4KB initial buffer size, the entire sample JSON is shown by each `Console.WriteLine`, and the buffer size never has to be increased.</span></span>

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/Utf8ReaderPartialRead.cs":::

<span data-ttu-id="55baa-169">L’exemple précédent n’affecte aucune limite à la taille maximale de la mémoire tampon.</span><span class="sxs-lookup"><span data-stu-id="55baa-169">The preceding example sets no limit to how large the buffer can grow.</span></span> <span data-ttu-id="55baa-170">Si la taille du jeton est trop grande, le code peut échouer avec une <xref:System.OutOfMemoryException> exception.</span><span class="sxs-lookup"><span data-stu-id="55baa-170">If the token size is too large, the code could fail with an <xref:System.OutOfMemoryException> exception.</span></span> <span data-ttu-id="55baa-171">Cela peut se produire si le JSON contient un jeton d’une taille d’environ 1 Go, car le doublement de la taille de 1 Go donne une taille trop importante pour tenir dans une `int32` mémoire tampon.</span><span class="sxs-lookup"><span data-stu-id="55baa-171">This can happen if the JSON contains a token that is around 1 GB or more in size, because doubling the 1 GB size results in a size that is too large to fit into an `int32` buffer.</span></span>

## <a name="see-also"></a><span data-ttu-id="55baa-172">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="55baa-172">See also</span></span>

* [<span data-ttu-id="55baa-173">System.Text.Json vue</span><span class="sxs-lookup"><span data-stu-id="55baa-173">System.Text.Json overview</span></span>](system-text-json-overview.md)
* [<span data-ttu-id="55baa-174">Comment personnaliser l’encodage de caractères</span><span class="sxs-lookup"><span data-stu-id="55baa-174">How to customize character encoding</span></span>](system-text-json-character-encoding.md)
* [<span data-ttu-id="55baa-175">Comment écrire des convertisseurs personnalisés pour la sérialisation JSON</span><span class="sxs-lookup"><span data-stu-id="55baa-175">How to write custom converters for JSON serialization</span></span>](system-text-json-converters-how-to.md)
* <span data-ttu-id="55baa-176">[System.Text.Json Référence d’API](xref:System.Text.Json)</span><span class="sxs-lookup"><span data-stu-id="55baa-176">[System.Text.Json API reference](xref:System.Text.Json)</span></span>
