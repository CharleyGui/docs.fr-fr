---
ms.openlocfilehash: 8a92a426ac2c5eee6fba40bfc46281420466d648
ms.sourcegitcommit: dfd612ba454ce775a766bcc6fe93bc1d43dfda47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/09/2019
ms.locfileid: "72237350"
---
### <a name="jsonelement-api-changes"></a><span data-ttu-id="81d92-101">Modifications de l’API JsonElement</span><span class="sxs-lookup"><span data-stu-id="81d92-101">JsonElement API changes</span></span>

<span data-ttu-id="81d92-102">À compter de .NET Core 3,0 Preview 7, certaines API <xref:System.Text.Json.JsonElement> ont été modifiées pour permettre une découverte plus facile et une plus grande facilité d’utilisation.</span><span class="sxs-lookup"><span data-stu-id="81d92-102">Starting with .NET Core 3.0 Preview 7, some <xref:System.Text.Json.JsonElement> APIs have changed to allow for easier discovery and greater usability.</span></span>

#### <a name="change-description"></a><span data-ttu-id="81d92-103">Modifier la description</span><span class="sxs-lookup"><span data-stu-id="81d92-103">Change description</span></span>

<span data-ttu-id="81d92-104">Dans .NET Core 3,0 Preview 7, les API <xref:System.Text.Json.JsonElement> ont été modifiées comme suit pour permettre une découverte plus facile et une plus grande facilité d’utilisation.</span><span class="sxs-lookup"><span data-stu-id="81d92-104">In .NET Core 3.0 Preview 7, <xref:System.Text.Json.JsonElement> APIs have changed as follows to allow for easier discovery and greater usability.</span></span>

1. <span data-ttu-id="81d92-105">Toutes les surcharges de méthode `WriteProperty` ont été supprimées de <xref:System.Text.Json.JsonElement>.</span><span class="sxs-lookup"><span data-stu-id="81d92-105">All `WriteProperty` method overloads were removed from <xref:System.Text.Json.JsonElement>.</span></span> <span data-ttu-id="81d92-106">Cela affecte le code comme suit :</span><span class="sxs-lookup"><span data-stu-id="81d92-106">This affects code such as the following:</span></span>

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

1. <span data-ttu-id="81d92-107">`WriteValue` a été renommé en <xref:System.Text.Json.JsonElement.WriteTo%2A>.</span><span class="sxs-lookup"><span data-stu-id="81d92-107">`WriteValue` was renamed as <xref:System.Text.Json.JsonElement.WriteTo%2A>.</span></span> <span data-ttu-id="81d92-108">Cela affecte le code comme suit :</span><span class="sxs-lookup"><span data-stu-id="81d92-108">This affects code such as the following:</span></span>

   ```csharp
    using (JsonDocument doc = JsonDocument.Parse(jsonString))
    {
        JsonElement root = doc.RootElement;
        root.WriteValue(writer);
    }
    ```

1. <span data-ttu-id="81d92-109"><xref:System.Text.Json.JsonElement.WriteTo%2A> lève désormais une <xref:System.ArgumentNullException> lorsque son paramètre de méthode est `null`.</span><span class="sxs-lookup"><span data-stu-id="81d92-109"><xref:System.Text.Json.JsonElement.WriteTo%2A> now throws an <xref:System.ArgumentNullException> when its method parameter is `null`.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="81d92-110">Version introduite</span><span class="sxs-lookup"><span data-stu-id="81d92-110">Version introduced</span></span>

<span data-ttu-id="81d92-111">3,0 Preview 7</span><span class="sxs-lookup"><span data-stu-id="81d92-111">3.0 Preview 7</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="81d92-112">Action recommandée</span><span class="sxs-lookup"><span data-stu-id="81d92-112">Recommended action</span></span>

<span data-ttu-id="81d92-113">Si votre code est affecté par ces modifications, vous pouvez effectuer les opérations suivantes :</span><span class="sxs-lookup"><span data-stu-id="81d92-113">If your code is affected by these changes, you can do the following:</span></span>

- <span data-ttu-id="81d92-114">Il n’existe aucune API de remplacement pour les surcharges `WriteProperty` dans <xref:System.Text.Json.JsonElement>.</span><span class="sxs-lookup"><span data-stu-id="81d92-114">There is no replacement API for the `WriteProperty` overloads in <xref:System.Text.Json.JsonElement>.</span></span> <span data-ttu-id="81d92-115">Au lieu de cela, vous pouvez appeler l’une des surcharges <xref:System.Text.Json.Utf8JsonWriter.WritePropertyName%2A?displayProperty=nameWithType>, ainsi que la méthode <xref:System.Text.Json.JsonElement.WriteTo%2A> pour Achive le même résultat.</span><span class="sxs-lookup"><span data-stu-id="81d92-115">Instead, you can call one of the <xref:System.Text.Json.Utf8JsonWriter.WritePropertyName%2A?displayProperty=nameWithType> overloads along with the <xref:System.Text.Json.JsonElement.WriteTo%2A> method to achive the same result.</span></span> <span data-ttu-id="81d92-116">Exemple :</span><span class="sxs-lookup"><span data-stu-id="81d92-116">For example:</span></span>

   ```csharp
   using (JsonDocument doc = JsonDocument.Parse(jsonString))
   {
       JsonElement root = doc.RootElement;
       writer.WritePropertyName(propertyNameString);
       root.WriteTo(writer);
   }
   ```

- <span data-ttu-id="81d92-117">Renommez la méthode `WriteValue` en <xref:System.Text.Json.JsonElement.WriteTo(System.Text.Json.Utf8JsonWriter)>.</span><span class="sxs-lookup"><span data-stu-id="81d92-117">Rename the `WriteValue` method to <xref:System.Text.Json.JsonElement.WriteTo(System.Text.Json.Utf8JsonWriter)>.</span></span> <span data-ttu-id="81d92-118">Le paramètre de la méthode reste inchangé.</span><span class="sxs-lookup"><span data-stu-id="81d92-118">The method parameter remains unchanged.</span></span> <span data-ttu-id="81d92-119">Par exemple, le code précédent doit être remplacé par ce qui suit :</span><span class="sxs-lookup"><span data-stu-id="81d92-119">For example, the previous code should be changed to the following:</span></span>

   ```csharp
   using (JsonDocument doc = JsonDocument.Parse(jsonString))
   {
       JsonElement root = doc.RootElement;
       root.WriteTo(writer);
   }
   ```

- <span data-ttu-id="81d92-120">Gérez le <xref:System.ArgumentNullException> dans les appels à la méthode <xref:System.Text.Json.JsonElement.WriteTo%2A>.</span><span class="sxs-lookup"><span data-stu-id="81d92-120">Handle the <xref:System.ArgumentNullException> in calls to the <xref:System.Text.Json.JsonElement.WriteTo%2A> method.</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="81d92-121">API affectées</span><span class="sxs-lookup"><span data-stu-id="81d92-121">Affected APIs</span></span>

- <xref:System.Text.Json.JsonElement>
- <xref:System.Text.Json.JsonElement.WriteTo%2A?displayProperty=nameWithType>

<!--

#### Affected APIs

- `Overload:System.Text.Json.JsonElement.WriteProperty`
- `M:System.Text.Json.JsonElement.WriteValue(System.Text.Json.Utf8JsonWriter)`

-->
