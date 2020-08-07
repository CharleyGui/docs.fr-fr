---
ms.openlocfilehash: 2e9267b35c9389da017927aca2346190348265c9
ms.sourcegitcommit: ef50c99928183a0bba75e07b9f22895cd4c480f8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/07/2020
ms.locfileid: "87919330"
---
### <a name="binaryformatterdeserialize-rewraps-some-exceptions-in-serializationexception"></a><span data-ttu-id="7a0cf-101">BinaryFormatter. Deserialize réencapsule certaines exceptions dans SerializationException</span><span class="sxs-lookup"><span data-stu-id="7a0cf-101">BinaryFormatter.Deserialize rewraps some exceptions in SerializationException</span></span>

<span data-ttu-id="7a0cf-102">La <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter.Deserialize%2A?displayProperty=nameWithType> méthode réencapsule maintenant certains objets d’exception à l’intérieur d’un <xref:System.Runtime.Serialization.SerializationException> avant de propager l’exception à l’appelant.</span><span class="sxs-lookup"><span data-stu-id="7a0cf-102">The <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter.Deserialize%2A?displayProperty=nameWithType> method now rewraps some exception objects inside a <xref:System.Runtime.Serialization.SerializationException> before propagating the exception back to the caller.</span></span>

#### <a name="change-description"></a><span data-ttu-id="7a0cf-103">Description de la modification</span><span class="sxs-lookup"><span data-stu-id="7a0cf-103">Change description</span></span>

<span data-ttu-id="7a0cf-104">Auparavant, la <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter.Deserialize%2A?displayProperty=nameWithType> méthode permettait des exceptions arbitraires, telles que <xref:System.ArgumentNullException> , pour propager la pile jusqu’à ses appelants.</span><span class="sxs-lookup"><span data-stu-id="7a0cf-104">Previously, the <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter.Deserialize%2A?displayProperty=nameWithType> method allowed some arbitrary exceptions, such as <xref:System.ArgumentNullException>, to propagate up the stack to its callers.</span></span>

<span data-ttu-id="7a0cf-105">Dans .NET 5,0 et versions ultérieures, la <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter.Deserialize%2A?displayProperty=nameWithType> méthode intercepte de manière plus agressive les exceptions qui se produisent en raison d’opérations de désérialisation non valides et les encapsule dans un <xref:System.Runtime.Serialization.SerializationException> .</span><span class="sxs-lookup"><span data-stu-id="7a0cf-105">In .NET 5.0 and later, the <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter.Deserialize%2A?displayProperty=nameWithType> method more aggressively catches exceptions that occur due to invalid deserialization operations and wraps them in a <xref:System.Runtime.Serialization.SerializationException>.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="7a0cf-106">Version introduite</span><span class="sxs-lookup"><span data-stu-id="7a0cf-106">Version introduced</span></span>

<span data-ttu-id="7a0cf-107">5,0 Preview 1</span><span class="sxs-lookup"><span data-stu-id="7a0cf-107">5.0 Preview 1</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="7a0cf-108">Action recommandée</span><span class="sxs-lookup"><span data-stu-id="7a0cf-108">Recommended action</span></span>

<span data-ttu-id="7a0cf-109">Dans la plupart des cas, vous n’avez aucune action à effectuer.</span><span class="sxs-lookup"><span data-stu-id="7a0cf-109">In most cases, you don't need to take any action.</span></span> <span data-ttu-id="7a0cf-110">Toutefois, si votre site d’appel dépend d’une exception particulière levée, vous pouvez désencapsuler l’exception du externe <xref:System.Runtime.Serialization.SerializationException> , comme illustré dans l’exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="7a0cf-110">However, if your call site depends on a particular exception being thrown, you can unwrap the exception from the outer <xref:System.Runtime.Serialization.SerializationException>, as shown in the following example.</span></span>

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

#### <a name="category"></a><span data-ttu-id="7a0cf-111">Category</span><span class="sxs-lookup"><span data-stu-id="7a0cf-111">Category</span></span>

<span data-ttu-id="7a0cf-112">Sérialisation</span><span class="sxs-lookup"><span data-stu-id="7a0cf-112">Serialization</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="7a0cf-113">API affectées</span><span class="sxs-lookup"><span data-stu-id="7a0cf-113">Affected APIs</span></span>

- <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter.Deserialize%2A?displayProperty=fullName>

<!--

#### Affected APIs

- `Overload:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter.Deserialize`

-->
