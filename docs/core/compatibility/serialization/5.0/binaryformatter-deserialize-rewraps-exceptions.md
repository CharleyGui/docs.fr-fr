---
title: 'Modification avec rupture : BinaryFormatter. Deserialize réencapsule certaines exceptions'
description: Découvrez la modification avec rupture dans .NET 5,0 où BinaryFormatter. Deserialize réencapsule certains objets d’exception à l’intérieur d’un SerializationException.
ms.date: 08/18/2020
ms.openlocfilehash: 90dc4cce6785fdb38644cca2a2e9aff65eb7a313
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95760920"
---
# <a name="binaryformatterdeserialize-rewraps-some-exceptions-in-serializationexception"></a><span data-ttu-id="9ebc4-103">BinaryFormatter. Deserialize réencapsule certaines exceptions dans SerializationException</span><span class="sxs-lookup"><span data-stu-id="9ebc4-103">BinaryFormatter.Deserialize rewraps some exceptions in SerializationException</span></span>

<span data-ttu-id="9ebc4-104">La <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter.Deserialize%2A?displayProperty=nameWithType> méthode réencapsule maintenant certains objets d’exception à l’intérieur d’un <xref:System.Runtime.Serialization.SerializationException> avant de propager l’exception à l’appelant.</span><span class="sxs-lookup"><span data-stu-id="9ebc4-104">The <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter.Deserialize%2A?displayProperty=nameWithType> method now rewraps some exception objects inside a <xref:System.Runtime.Serialization.SerializationException> before propagating the exception back to the caller.</span></span>

## <a name="change-description"></a><span data-ttu-id="9ebc4-105">Description de la modification</span><span class="sxs-lookup"><span data-stu-id="9ebc4-105">Change description</span></span>

<span data-ttu-id="9ebc4-106">Auparavant, la <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter.Deserialize%2A?displayProperty=nameWithType> méthode permettait des exceptions arbitraires, telles que <xref:System.ArgumentNullException> , pour propager la pile jusqu’à ses appelants.</span><span class="sxs-lookup"><span data-stu-id="9ebc4-106">Previously, the <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter.Deserialize%2A?displayProperty=nameWithType> method allowed some arbitrary exceptions, such as <xref:System.ArgumentNullException>, to propagate up the stack to its callers.</span></span>

<span data-ttu-id="9ebc4-107">Dans .NET 5,0 et versions ultérieures, la <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter.Deserialize%2A?displayProperty=nameWithType> méthode intercepte de manière plus agressive les exceptions qui se produisent en raison d’opérations de désérialisation non valides et les encapsule dans un <xref:System.Runtime.Serialization.SerializationException> .</span><span class="sxs-lookup"><span data-stu-id="9ebc4-107">In .NET 5.0 and later, the <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter.Deserialize%2A?displayProperty=nameWithType> method more aggressively catches exceptions that occur due to invalid deserialization operations and wraps them in a <xref:System.Runtime.Serialization.SerializationException>.</span></span>

## <a name="version-introduced"></a><span data-ttu-id="9ebc4-108">Version introduite</span><span class="sxs-lookup"><span data-stu-id="9ebc4-108">Version introduced</span></span>

<span data-ttu-id="9ebc4-109">5.0</span><span class="sxs-lookup"><span data-stu-id="9ebc4-109">5.0</span></span>

## <a name="recommended-action"></a><span data-ttu-id="9ebc4-110">Action recommandée</span><span class="sxs-lookup"><span data-stu-id="9ebc4-110">Recommended action</span></span>

<span data-ttu-id="9ebc4-111">Dans la plupart des cas, vous n’avez aucune action à effectuer.</span><span class="sxs-lookup"><span data-stu-id="9ebc4-111">In most cases, you don't need to take any action.</span></span> <span data-ttu-id="9ebc4-112">Toutefois, si votre site d’appel dépend d’une exception particulière levée, vous pouvez désencapsuler l’exception du externe <xref:System.Runtime.Serialization.SerializationException> , comme illustré dans l’exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="9ebc4-112">However, if your call site depends on a particular exception being thrown, you can unwrap the exception from the outer <xref:System.Runtime.Serialization.SerializationException>, as shown in the following example.</span></span>

```csharp
Stream inputStream = GetInputStream();
var formatter = new BinaryFormatter();

try
{
    object deserialized = formatter.Deserialize(inputStream);
}
catch (MyException myEx)
{
    // Handle 'myEx' here in case it was thrown directly.
}
catch (SerializationException serEx) when (serEx.InnerException is MyException myEx)
{
    // Handle 'myEx' here in case it was wrapped in SerializationException.
}
```

## <a name="affected-apis"></a><span data-ttu-id="9ebc4-113">API affectées</span><span class="sxs-lookup"><span data-stu-id="9ebc4-113">Affected APIs</span></span>

- <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter.Deserialize%2A?displayProperty=fullName>

<!--

### Affected APIs

- `Overload:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter.Deserialize`

### Category

Serialization

-->
