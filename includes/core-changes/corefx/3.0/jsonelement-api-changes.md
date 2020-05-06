---
ms.openlocfilehash: 79901d0b57816915ca7ea73cfe7fa3d40820434e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "74568167"
---
### <a name="jsonelement-api-changes"></a><span data-ttu-id="d19c9-101">Modifications de l’API JsonElement</span><span class="sxs-lookup"><span data-stu-id="d19c9-101">JsonElement API changes</span></span>

<span data-ttu-id="d19c9-102">À compter de .NET Core 3,0 Preview 7, <xref:System.Text.Json.JsonElement> certaines API ont été modifiées pour permettre une découverte plus facile et une plus grande facilité d’utilisation.</span><span class="sxs-lookup"><span data-stu-id="d19c9-102">Starting with .NET Core 3.0 Preview 7, some <xref:System.Text.Json.JsonElement> APIs have changed to allow for easier discovery and greater usability.</span></span>

#### <a name="change-description"></a><span data-ttu-id="d19c9-103">Description de la modification</span><span class="sxs-lookup"><span data-stu-id="d19c9-103">Change description</span></span>

<span data-ttu-id="d19c9-104">Dans .NET Core 3,0 Preview 7, <xref:System.Text.Json.JsonElement> les API ont été modifiées comme suit pour permettre une découverte plus facile et une plus grande facilité d’utilisation.</span><span class="sxs-lookup"><span data-stu-id="d19c9-104">In .NET Core 3.0 Preview 7, <xref:System.Text.Json.JsonElement> APIs have changed as follows to allow for easier discovery and greater usability.</span></span>

1. <span data-ttu-id="d19c9-105">Toutes `WriteProperty` les surcharges de méthode ont <xref:System.Text.Json.JsonElement>été supprimées de.</span><span class="sxs-lookup"><span data-stu-id="d19c9-105">All `WriteProperty` method overloads were removed from <xref:System.Text.Json.JsonElement>.</span></span> <span data-ttu-id="d19c9-106">Cela affecte le code comme suit :</span><span class="sxs-lookup"><span data-stu-id="d19c9-106">This affects code such as the following:</span></span>

   ```csharp
   using (JsonDocument doc = JsonDocument.Parse(jsonString))
   {
      JsonElement root = doc.RootElement;
      root.WriteProperty(propertyNameString, writer);
      // ..
      root.WriteProperty(propertyNameSpan, writer);
      // ..
      root.WriteProperty(propertyNameJsonEncoded, writer);
      // ..
      root.WriteProperty(utf8PropertyName, writer);
      //..
   }
   ```

1. <span data-ttu-id="d19c9-107">`WriteValue`a été renommé en <xref:System.Text.Json.JsonElement.WriteTo%2A>.</span><span class="sxs-lookup"><span data-stu-id="d19c9-107">`WriteValue` was renamed as <xref:System.Text.Json.JsonElement.WriteTo%2A>.</span></span> <span data-ttu-id="d19c9-108">Cela affecte le code comme suit :</span><span class="sxs-lookup"><span data-stu-id="d19c9-108">This affects code such as the following:</span></span>

   ```csharp
    using (JsonDocument doc = JsonDocument.Parse(jsonString))
    {
        JsonElement root = doc.RootElement;
        root.WriteValue(writer);
    }
    ```

1. <span data-ttu-id="d19c9-109"><xref:System.Text.Json.JsonElement.WriteTo%2A>lève désormais une <xref:System.ArgumentNullException> lorsque son paramètre de méthode est `null`.</span><span class="sxs-lookup"><span data-stu-id="d19c9-109"><xref:System.Text.Json.JsonElement.WriteTo%2A> now throws an <xref:System.ArgumentNullException> when its method parameter is `null`.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="d19c9-110">Version introduite</span><span class="sxs-lookup"><span data-stu-id="d19c9-110">Version introduced</span></span>

<span data-ttu-id="d19c9-111">3,0 Preview 7</span><span class="sxs-lookup"><span data-stu-id="d19c9-111">3.0 Preview 7</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="d19c9-112">Action recommandée</span><span class="sxs-lookup"><span data-stu-id="d19c9-112">Recommended action</span></span>

<span data-ttu-id="d19c9-113">Si votre code est affecté par ces modifications, vous pouvez effectuer les opérations suivantes :</span><span class="sxs-lookup"><span data-stu-id="d19c9-113">If your code is affected by these changes, you can do the following:</span></span>

- <span data-ttu-id="d19c9-114">Il n’existe aucune API de remplacement `WriteProperty` pour les surcharges dans <xref:System.Text.Json.JsonElement>.</span><span class="sxs-lookup"><span data-stu-id="d19c9-114">There is no replacement API for the `WriteProperty` overloads in <xref:System.Text.Json.JsonElement>.</span></span> <span data-ttu-id="d19c9-115">Au lieu de cela, vous pouvez appeler <xref:System.Text.Json.Utf8JsonWriter.WritePropertyName%2A?displayProperty=nameWithType> l’une des surcharges <xref:System.Text.Json.JsonElement.WriteTo%2A> avec la méthode pour obtenir le même résultat.</span><span class="sxs-lookup"><span data-stu-id="d19c9-115">Instead, you can call one of the <xref:System.Text.Json.Utf8JsonWriter.WritePropertyName%2A?displayProperty=nameWithType> overloads along with the <xref:System.Text.Json.JsonElement.WriteTo%2A> method to achieve the same result.</span></span> <span data-ttu-id="d19c9-116">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="d19c9-116">For example:</span></span>

   ```csharp
   using (JsonDocument doc = JsonDocument.Parse(jsonString))
   {
       JsonElement root = doc.RootElement;
       writer.WritePropertyName(propertyNameString);
       root.WriteTo(writer);
   }
   ```

- <span data-ttu-id="d19c9-117">Renommez `WriteValue` la méthode <xref:System.Text.Json.JsonElement.WriteTo(System.Text.Json.Utf8JsonWriter)>en.</span><span class="sxs-lookup"><span data-stu-id="d19c9-117">Rename the `WriteValue` method to <xref:System.Text.Json.JsonElement.WriteTo(System.Text.Json.Utf8JsonWriter)>.</span></span> <span data-ttu-id="d19c9-118">Le paramètre de la méthode reste inchangé.</span><span class="sxs-lookup"><span data-stu-id="d19c9-118">The method parameter remains unchanged.</span></span> <span data-ttu-id="d19c9-119">Par exemple, le code précédent doit être remplacé par ce qui suit :</span><span class="sxs-lookup"><span data-stu-id="d19c9-119">For example, the previous code should be changed to the following:</span></span>

   ```csharp
   using (JsonDocument doc = JsonDocument.Parse(jsonString))
   {
       JsonElement root = doc.RootElement;
       root.WriteTo(writer);
   }
   ```

- <span data-ttu-id="d19c9-120">Gérez les <xref:System.ArgumentNullException> dans les appels à <xref:System.Text.Json.JsonElement.WriteTo%2A> la méthode.</span><span class="sxs-lookup"><span data-stu-id="d19c9-120">Handle the <xref:System.ArgumentNullException> in calls to the <xref:System.Text.Json.JsonElement.WriteTo%2A> method.</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="d19c9-121">API affectées</span><span class="sxs-lookup"><span data-stu-id="d19c9-121">Affected APIs</span></span>

- <xref:System.Text.Json.JsonElement>
- <xref:System.Text.Json.JsonElement.WriteTo%2A?displayProperty=nameWithType>

<!--

#### Affected APIs

- `Overload:System.Text.Json.JsonElement.WriteProperty`
- `M:System.Text.Json.JsonElement.WriteValue(System.Text.Json.Utf8JsonWriter)`

-->
