---
title: Messages Protobuf - gRPC pour les développeurs WCF
description: Découvrez comment les messages Protobuf sont définis dans l’IDL et générés en C.
ms.date: 09/09/2019
ms.openlocfilehash: 5b3d4383de39a3785ef804fec21939a740f54669
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79147982"
---
# <a name="protobuf-messages"></a><span data-ttu-id="c111c-103">Messages Protobuf</span><span class="sxs-lookup"><span data-stu-id="c111c-103">Protobuf messages</span></span>

<span data-ttu-id="c111c-104">Cette section couvre la façon de déclarer les `.proto` messages De mémoire tampon (Protobuf) dans les fichiers.</span><span class="sxs-lookup"><span data-stu-id="c111c-104">This section covers how to declare Protocol Buffer (Protobuf) messages in `.proto` files.</span></span> <span data-ttu-id="c111c-105">Il explique les concepts fondamentaux des nombres et des types `protoc` de terrain, et il examine le code Cmd que le compilateur génère.</span><span class="sxs-lookup"><span data-stu-id="c111c-105">It explains the fundamental concepts of field numbers and types, and it looks at the C# code that the `protoc` compiler generates.</span></span>

<span data-ttu-id="c111c-106">Le reste du chapitre examinera plus en détail comment différents types de données sont représentés dans Protobuf.</span><span class="sxs-lookup"><span data-stu-id="c111c-106">The rest of the chapter will look in more detail at how different types of data are represented in Protobuf.</span></span>

## <a name="declaring-a-message"></a><span data-ttu-id="c111c-107">Déclarer un message</span><span class="sxs-lookup"><span data-stu-id="c111c-107">Declaring a message</span></span>

<span data-ttu-id="c111c-108">Dans Windows Communication Foundation (WCF), une `Stock` classe pour une application de négociation boursière peut être définie comme l’exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="c111c-108">In Windows Communication Foundation (WCF), a `Stock` class for a stock market trading application might be defined like the following example:</span></span>

```csharp
namespace TraderSys
{
    [DataContract]
    public class Stock
    {
        [DataMember]
        public int Id { get; set;}
        [DataMember]
        public string Symbol { get; set;}
        [DataMember]
        public string DisplayName { get; set;}
        [DataMember]
        public int MarketId { get; set; }
    }
}
```

<span data-ttu-id="c111c-109">Pour implémenter la classe équivalente dans `.proto` Protobuf, vous devez la déclarer dans le fichier.</span><span class="sxs-lookup"><span data-stu-id="c111c-109">To implement the equivalent class in Protobuf, you must declare it in the `.proto` file.</span></span> <span data-ttu-id="c111c-110">Le `protoc` compilateur générera ensuite la classe .NET dans le cadre du processus de construction.</span><span class="sxs-lookup"><span data-stu-id="c111c-110">The `protoc` compiler will then generate the .NET class as part of the build process.</span></span>

```protobuf
syntax "proto3";

option csharp_namespace = "TraderSys";

message Stock {

    int32 id = 1;
    string symbol = 2;
    string display_name = 3;
    int32 market_id = 4;

}  
```

<span data-ttu-id="c111c-111">La première ligne déclare la version syntaxe utilisée.</span><span class="sxs-lookup"><span data-stu-id="c111c-111">The first line declares the syntax version being used.</span></span> <span data-ttu-id="c111c-112">La version 3 de la langue est sortie en 2016.</span><span class="sxs-lookup"><span data-stu-id="c111c-112">Version 3 of the language was released in 2016.</span></span> <span data-ttu-id="c111c-113">C’est la version que nous recommandons pour les services gRPC.</span><span class="sxs-lookup"><span data-stu-id="c111c-113">It's the version that we recommend for gRPC services.</span></span>

<span data-ttu-id="c111c-114">La `option csharp_namespace` ligne spécifie l’espace nom à utiliser pour les types C générés.</span><span class="sxs-lookup"><span data-stu-id="c111c-114">The `option csharp_namespace` line specifies the namespace to be used for the generated C# types.</span></span> <span data-ttu-id="c111c-115">Cette option sera ignorée lorsque le `.proto` fichier sera compilé pour d’autres langues.</span><span class="sxs-lookup"><span data-stu-id="c111c-115">This option will be ignored when the `.proto` file is compiled for other languages.</span></span> <span data-ttu-id="c111c-116">Les fichiers Protobuf contiennent souvent des options spécifiques à la langue pour plusieurs langues.</span><span class="sxs-lookup"><span data-stu-id="c111c-116">Protobuf files often contain language-specific options for several languages.</span></span>

<span data-ttu-id="c111c-117">La `Stock` définition du message spécifie quatre champs.</span><span class="sxs-lookup"><span data-stu-id="c111c-117">The `Stock` message definition specifies four fields.</span></span> <span data-ttu-id="c111c-118">Chacun a un type, un nom et un numéro de champ.</span><span class="sxs-lookup"><span data-stu-id="c111c-118">Each has a type, a name, and a field number.</span></span>

## <a name="field-numbers"></a><span data-ttu-id="c111c-119">Numéros de terrain</span><span class="sxs-lookup"><span data-stu-id="c111c-119">Field numbers</span></span>

<span data-ttu-id="c111c-120">Les numéros de terrain sont une partie importante de Protobuf.</span><span class="sxs-lookup"><span data-stu-id="c111c-120">Field numbers are an important part of Protobuf.</span></span> <span data-ttu-id="c111c-121">Ils sont utilisés pour identifier les champs dans les données codées binaires, ce qui signifie qu’ils ne peuvent pas changer de la version à la version de votre service.</span><span class="sxs-lookup"><span data-stu-id="c111c-121">They're used to identify fields in the binary encoded data, which means they can't change from version to version of your service.</span></span> <span data-ttu-id="c111c-122">L’avantage est que la compatibilité vers l’arrière et la compatibilité vers l’avant sont possibles.</span><span class="sxs-lookup"><span data-stu-id="c111c-122">The advantage is that backward compatibility and forward compatibility are possible.</span></span> <span data-ttu-id="c111c-123">Les clients et les services ignoreront simplement les numéros de terrain qu’ils ne connaissent pas, tant que la possibilité de manquer des valeurs est gérée.</span><span class="sxs-lookup"><span data-stu-id="c111c-123">Clients and services will simply ignore field numbers that they don't know about, as long as the possibility of missing values is handled.</span></span>

<span data-ttu-id="c111c-124">Dans le format binaire, le numéro de champ est combiné avec un identifiant de type.</span><span class="sxs-lookup"><span data-stu-id="c111c-124">In the binary format, the field number is combined with a type identifier.</span></span> <span data-ttu-id="c111c-125">Les numéros de champ de 1 à 15 peuvent être codés avec leur type comme un seul byte.</span><span class="sxs-lookup"><span data-stu-id="c111c-125">Field numbers from 1 to 15 can be encoded with their type as a single byte.</span></span> <span data-ttu-id="c111c-126">Les numéros de 16 à 2 047 prennent 2 octets.</span><span class="sxs-lookup"><span data-stu-id="c111c-126">Numbers from 16 to 2,047 take 2 bytes.</span></span> <span data-ttu-id="c111c-127">Vous pouvez aller plus haut si vous avez besoin de plus de 2 047 champs sur un message pour n’importe quelle raison.</span><span class="sxs-lookup"><span data-stu-id="c111c-127">You can go higher if you need more than 2,047 fields on a message for any reason.</span></span> <span data-ttu-id="c111c-128">Les identifiants d’endo unique pour les numéros de champ 1 à 15 offrent de meilleures performances, de sorte que vous devriez les utiliser pour les champs les plus basiques, fréquemment utilisés.</span><span class="sxs-lookup"><span data-stu-id="c111c-128">The single byte identifiers for field numbers 1 to 15 offer better performance, so you should use them for the most basic, frequently used fields.</span></span>

## <a name="types"></a><span data-ttu-id="c111c-129">Types</span><span class="sxs-lookup"><span data-stu-id="c111c-129">Types</span></span>

<span data-ttu-id="c111c-130">Les déclarations de type utilisent les types de données scalaires indigènes de Protobuf, qui sont discutés plus en détail dans [la section suivante](protobuf-data-types.md).</span><span class="sxs-lookup"><span data-stu-id="c111c-130">The type declarations are using Protobuf's native scalar data types, which are discussed in more detail in [the next section](protobuf-data-types.md).</span></span> <span data-ttu-id="c111c-131">Le reste de ce chapitre couvrira les types intégrés de Protobuf et montrera comment ils se rapportent aux types .NET communs.</span><span class="sxs-lookup"><span data-stu-id="c111c-131">The rest of this chapter will cover Protobuf's built-in types and show how they relate to common .NET types.</span></span>

> [!NOTE]
> <span data-ttu-id="c111c-132">Protobuf ne supporte pas `decimal` un `double` type natif, est donc utilisé à la place.</span><span class="sxs-lookup"><span data-stu-id="c111c-132">Protobuf doesn't natively support a `decimal` type, so `double` is used instead.</span></span> <span data-ttu-id="c111c-133">Pour les applications qui nécessitent une précision décimale complète, se référer à la [section sur les décimales](protobuf-data-types.md#decimals) dans la prochaine partie de ce chapitre.</span><span class="sxs-lookup"><span data-stu-id="c111c-133">For applications that require full decimal precision, refer to the [section on decimals](protobuf-data-types.md#decimals) in the next part of this chapter.</span></span>

## <a name="the-generated-code"></a><span data-ttu-id="c111c-134">Code généré</span><span class="sxs-lookup"><span data-stu-id="c111c-134">The generated code</span></span>

<span data-ttu-id="c111c-135">Lorsque vous construisez votre application, Protobuf crée des classes pour chacun de vos messages, cartographiant ses types natifs en types C.</span><span class="sxs-lookup"><span data-stu-id="c111c-135">When you build your application, Protobuf creates classes for each of your messages, mapping its native types to C# types.</span></span> <span data-ttu-id="c111c-136">Le `Stock` type généré aurait la signature suivante :</span><span class="sxs-lookup"><span data-stu-id="c111c-136">The generated `Stock` type would have the following signature:</span></span>

```csharp
public class Stock
{
    public int Id { get; set; }
    public string Symbol { get; set; }
    public string DisplayName { get; set; }
    public int MarketId { get; set; }
}
```

<span data-ttu-id="c111c-137">Le code réel qui est généré est beaucoup plus compliqué que cela.</span><span class="sxs-lookup"><span data-stu-id="c111c-137">The actual code that's generated is far more complicated than this.</span></span> <span data-ttu-id="c111c-138">La raison en est que chaque classe contient tout le code nécessaire pour sérialiser et se déséialiser au format de fil binaire.</span><span class="sxs-lookup"><span data-stu-id="c111c-138">The reason is that each class contains all the code necessary to serialize and deserialize itself to the binary wire format.</span></span>

### <a name="property-names"></a><span data-ttu-id="c111c-139">Noms de propriété</span><span class="sxs-lookup"><span data-stu-id="c111c-139">Property names</span></span>

<span data-ttu-id="c111c-140">Notez que le compilateur `PascalCase` Protobuf s’est `snake_case` appliqué `.proto` aux noms de propriété, bien qu’ils étaient dans le fichier.</span><span class="sxs-lookup"><span data-stu-id="c111c-140">Note that the Protobuf compiler applied `PascalCase` to the property names, although they were `snake_case` in the `.proto` file.</span></span> <span data-ttu-id="c111c-141">Le [guide de style Protobuf](https://developers.google.com/protocol-buffers/docs/style) recommande d’utiliser `snake_case` dans vos définitions de messages afin que la génération de code pour d’autres plates-formes produise le cas prévu pour leurs conventions.</span><span class="sxs-lookup"><span data-stu-id="c111c-141">The [Protobuf style guide](https://developers.google.com/protocol-buffers/docs/style) recommends using `snake_case` in your message definitions so that the code generation for other platforms produces the expected case for their conventions.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="c111c-142">[Suivant précédent](protocol-buffers.md)
>[Next](protobuf-data-types.md)</span><span class="sxs-lookup"><span data-stu-id="c111c-142">[Previous](protocol-buffers.md)
[Next](protobuf-data-types.md)</span></span>
