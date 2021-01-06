---
title: Messages Protobuf-gRPC pour les développeurs WCF
description: Découvrez comment les messages Protobuf sont définis dans l’IDL et générés en C#.
ms.date: 12/15/2020
ms.openlocfilehash: c1f2a3071d45dcbe4b98d747f19fed508bad102f
ms.sourcegitcommit: 655f8a16c488567dfa696fc0b293b34d3c81e3df
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/06/2021
ms.locfileid: "97938102"
---
# <a name="protobuf-messages"></a><span data-ttu-id="c8ed7-103">Messages Protobuf</span><span class="sxs-lookup"><span data-stu-id="c8ed7-103">Protobuf messages</span></span>

<span data-ttu-id="c8ed7-104">Cette section explique comment déclarer des messages de tampon de protocole (Protobuf) dans des `.proto` fichiers.</span><span class="sxs-lookup"><span data-stu-id="c8ed7-104">This section covers how to declare Protocol Buffer (Protobuf) messages in `.proto` files.</span></span> <span data-ttu-id="c8ed7-105">Il explique les concepts fondamentaux des nombres de champs et des types, et il examine le code C# généré par le `protoc` compilateur.</span><span class="sxs-lookup"><span data-stu-id="c8ed7-105">It explains the fundamental concepts of field numbers and types, and it looks at the C# code that the `protoc` compiler generates.</span></span>

<span data-ttu-id="c8ed7-106">Le reste du chapitre aborde plus en détail la façon dont les différents types de données sont représentés dans Protobuf.</span><span class="sxs-lookup"><span data-stu-id="c8ed7-106">The rest of the chapter will look in more detail at how different types of data are represented in Protobuf.</span></span>

## <a name="declaring-a-message"></a><span data-ttu-id="c8ed7-107">Déclaration d’un message</span><span class="sxs-lookup"><span data-stu-id="c8ed7-107">Declaring a message</span></span>

<span data-ttu-id="c8ed7-108">Dans Windows Communication Foundation (WCF), une `Stock` classe pour une application commerciale boursière peut être définie comme dans l’exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="c8ed7-108">In Windows Communication Foundation (WCF), a `Stock` class for a stock market trading application might be defined like the following example:</span></span>

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

<span data-ttu-id="c8ed7-109">Pour implémenter la classe équivalente dans Protobuf, vous devez la déclarer dans le `.proto` fichier.</span><span class="sxs-lookup"><span data-stu-id="c8ed7-109">To implement the equivalent class in Protobuf, you must declare it in the `.proto` file.</span></span> <span data-ttu-id="c8ed7-110">Le `protoc` compilateur génère ensuite la classe .net dans le cadre du processus de génération.</span><span class="sxs-lookup"><span data-stu-id="c8ed7-110">The `protoc` compiler will then generate the .NET class as part of the build process.</span></span>

```protobuf
syntax = "proto3";

option csharp_namespace = "TraderSys";

message Stock {

    int32 id = 1;
    string symbol = 2;
    string display_name = 3;
    int32 market_id = 4;

}  
```

<span data-ttu-id="c8ed7-111">La première ligne déclare la version de syntaxe utilisée.</span><span class="sxs-lookup"><span data-stu-id="c8ed7-111">The first line declares the syntax version being used.</span></span> <span data-ttu-id="c8ed7-112">La version 3 de la langue a été publiée en 2016.</span><span class="sxs-lookup"><span data-stu-id="c8ed7-112">Version 3 of the language was released in 2016.</span></span> <span data-ttu-id="c8ed7-113">C’est la version que nous recommandons pour les services gRPC.</span><span class="sxs-lookup"><span data-stu-id="c8ed7-113">It's the version that we recommend for gRPC services.</span></span>

<span data-ttu-id="c8ed7-114">La `option csharp_namespace` ligne spécifie l’espace de noms à utiliser pour les types C# générés.</span><span class="sxs-lookup"><span data-stu-id="c8ed7-114">The `option csharp_namespace` line specifies the namespace to be used for the generated C# types.</span></span> <span data-ttu-id="c8ed7-115">Cette option est ignorée lorsque le `.proto` fichier est compilé pour d’autres langues.</span><span class="sxs-lookup"><span data-stu-id="c8ed7-115">This option will be ignored when the `.proto` file is compiled for other languages.</span></span> <span data-ttu-id="c8ed7-116">Les fichiers Protobuf contiennent souvent des options spécifiques à la langue pour plusieurs langues.</span><span class="sxs-lookup"><span data-stu-id="c8ed7-116">Protobuf files often contain language-specific options for several languages.</span></span>

<span data-ttu-id="c8ed7-117">La `Stock` définition du message spécifie quatre champs.</span><span class="sxs-lookup"><span data-stu-id="c8ed7-117">The `Stock` message definition specifies four fields.</span></span> <span data-ttu-id="c8ed7-118">Chaque a un type, un nom et un numéro de champ.</span><span class="sxs-lookup"><span data-stu-id="c8ed7-118">Each has a type, a name, and a field number.</span></span>

## <a name="field-numbers"></a><span data-ttu-id="c8ed7-119">Numéros de champ</span><span class="sxs-lookup"><span data-stu-id="c8ed7-119">Field numbers</span></span>

<span data-ttu-id="c8ed7-120">Les numéros de champ constituent une partie importante de Protobuf.</span><span class="sxs-lookup"><span data-stu-id="c8ed7-120">Field numbers are an important part of Protobuf.</span></span> <span data-ttu-id="c8ed7-121">Elles sont utilisées pour identifier les champs dans les données binaires codées, ce qui signifie qu’elles ne peuvent pas passer d’une version à une version de votre service.</span><span class="sxs-lookup"><span data-stu-id="c8ed7-121">They're used to identify fields in the binary encoded data, which means they can't change from version to version of your service.</span></span> <span data-ttu-id="c8ed7-122">L’avantage est que la compatibilité descendante et la compatibilité ascendante sont possibles.</span><span class="sxs-lookup"><span data-stu-id="c8ed7-122">The advantage is that backward compatibility and forward compatibility are possible.</span></span> <span data-ttu-id="c8ed7-123">Les clients et les services ignorent les numéros de champ qu’ils ne connaissent pas, à condition que la possibilité de valeurs manquantes soit gérée.</span><span class="sxs-lookup"><span data-stu-id="c8ed7-123">Clients and services will ignore field numbers that they don't know about, as long as the possibility of missing values is handled.</span></span>

<span data-ttu-id="c8ed7-124">Dans le format binaire, le numéro de champ est associé à un identificateur de type.</span><span class="sxs-lookup"><span data-stu-id="c8ed7-124">In the binary format, the field number is combined with a type identifier.</span></span> <span data-ttu-id="c8ed7-125">Les numéros de champ de 1 à 15 peuvent être encodés avec leur type comme un seul octet.</span><span class="sxs-lookup"><span data-stu-id="c8ed7-125">Field numbers from 1 to 15 can be encoded with their type as a single byte.</span></span> <span data-ttu-id="c8ed7-126">Les nombres compris entre 16 et 2 047 prennent 2 octets.</span><span class="sxs-lookup"><span data-stu-id="c8ed7-126">Numbers from 16 to 2,047 take 2 bytes.</span></span> <span data-ttu-id="c8ed7-127">Vous pouvez aller plus haut si vous avez besoin de plus de 2 047 champs sur un message pour une raison quelconque.</span><span class="sxs-lookup"><span data-stu-id="c8ed7-127">You can go higher if you need more than 2,047 fields on a message for any reason.</span></span> <span data-ttu-id="c8ed7-128">Les identificateurs sur un octet pour les numéros de champ 1 à 15 offrent de meilleures performances. vous devez donc les utiliser pour les champs les plus basiques et les plus fréquemment utilisés.</span><span class="sxs-lookup"><span data-stu-id="c8ed7-128">The single-byte identifiers for field numbers 1 to 15 offer better performance, so you should use them for the most basic, frequently used fields.</span></span>

## <a name="types"></a><span data-ttu-id="c8ed7-129">Types</span><span class="sxs-lookup"><span data-stu-id="c8ed7-129">Types</span></span>

<span data-ttu-id="c8ed7-130">Les déclarations de type utilisent les types de données scalaires natives de Protobuf, qui sont décrits plus en détail dans [la section suivante](protobuf-data-types.md).</span><span class="sxs-lookup"><span data-stu-id="c8ed7-130">The type declarations are using Protobuf's native scalar data types, which are discussed in more detail in [the next section](protobuf-data-types.md).</span></span> <span data-ttu-id="c8ed7-131">Le reste de ce chapitre traite des types intégrés de Protobuf et montre comment ils se rapportent aux types .NET courants.</span><span class="sxs-lookup"><span data-stu-id="c8ed7-131">The rest of this chapter will cover Protobuf's built-in types and show how they relate to common .NET types.</span></span>

> [!NOTE]
> <span data-ttu-id="c8ed7-132">Protobuf ne prend pas en charge de manière native un `decimal` type, donc `double` est utilisé à la place.</span><span class="sxs-lookup"><span data-stu-id="c8ed7-132">Protobuf doesn't natively support a `decimal` type, so `double` is used instead.</span></span> <span data-ttu-id="c8ed7-133">Pour les applications qui requièrent une précision décimale complète, reportez-vous à la [section sur les décimales](protobuf-data-types.md#decimals) dans la partie suivante de ce chapitre.</span><span class="sxs-lookup"><span data-stu-id="c8ed7-133">For applications that require full decimal precision, refer to the [section on decimals](protobuf-data-types.md#decimals) in the next part of this chapter.</span></span>

## <a name="the-generated-code"></a><span data-ttu-id="c8ed7-134">Code généré</span><span class="sxs-lookup"><span data-stu-id="c8ed7-134">The generated code</span></span>

<span data-ttu-id="c8ed7-135">Quand vous générez votre application, Protobuf crée des classes pour chacun de vos messages, en mappant ses types natifs aux types C#.</span><span class="sxs-lookup"><span data-stu-id="c8ed7-135">When you build your application, Protobuf creates classes for each of your messages, mapping its native types to C# types.</span></span> <span data-ttu-id="c8ed7-136">Le `Stock` type généré aurait la signature suivante :</span><span class="sxs-lookup"><span data-stu-id="c8ed7-136">The generated `Stock` type would have the following signature:</span></span>

```csharp
public class Stock
{
    public int Id { get; set; }
    public string Symbol { get; set; }
    public string DisplayName { get; set; }
    public int MarketId { get; set; }
}
```

<span data-ttu-id="c8ed7-137">Le code réel qui est généré est beaucoup plus complexe que celui-ci.</span><span class="sxs-lookup"><span data-stu-id="c8ed7-137">The actual code that's generated is far more complicated than this.</span></span> <span data-ttu-id="c8ed7-138">La raison en est que chaque classe contient tout le code nécessaire pour sérialiser et désérialiser lui-même au format de câble binaire.</span><span class="sxs-lookup"><span data-stu-id="c8ed7-138">The reason is that each class contains all the code necessary to serialize and deserialize itself to the binary wire format.</span></span>

### <a name="property-names"></a><span data-ttu-id="c8ed7-139">Noms des propriétés</span><span class="sxs-lookup"><span data-stu-id="c8ed7-139">Property names</span></span>

<span data-ttu-id="c8ed7-140">Notez que le compilateur Protobuf appliqué `PascalCase` aux noms de propriété, même s’ils se trouvaient `snake_case` dans le `.proto` fichier.</span><span class="sxs-lookup"><span data-stu-id="c8ed7-140">Note that the Protobuf compiler applied `PascalCase` to the property names, although they were `snake_case` in the `.proto` file.</span></span> <span data-ttu-id="c8ed7-141">Le [Guide de style Protobuf](https://developers.google.com/protocol-buffers/docs/style) recommande l’utilisation `snake_case` de dans vos définitions de message afin que la génération de code pour d’autres plateformes produise la casse attendue pour leurs conventions.</span><span class="sxs-lookup"><span data-stu-id="c8ed7-141">The [Protobuf style guide](https://developers.google.com/protocol-buffers/docs/style) recommends using `snake_case` in your message definitions so that the code generation for other platforms produces the expected case for their conventions.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="c8ed7-142">[Précédent](protocol-buffers.md) 
> [Suivant](protobuf-data-types.md)</span><span class="sxs-lookup"><span data-stu-id="c8ed7-142">[Previous](protocol-buffers.md)
[Next](protobuf-data-types.md)</span></span>
