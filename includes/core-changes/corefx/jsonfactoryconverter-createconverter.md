---
ms.openlocfilehash: e16f0c8ede5e1a24d4fc4606c3c25225ea72e750
ms.sourcegitcommit: a4b10e1f2a8bb4e8ff902630855474a0c4f1b37a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/19/2019
ms.locfileid: "71117088"
---
### <a name="jsonfactoryconvertercreateconverter-signature-changed"></a><span data-ttu-id="a8d80-101">Signature de JsonFactoryConverter. CreateConverter modifiée</span><span class="sxs-lookup"><span data-stu-id="a8d80-101">JsonFactoryConverter.CreateConverter signature changed</span></span>

<span data-ttu-id="a8d80-102">Pour faciliter la composition des <xref:System.Text.Json.Serialization.JsonConverterFactory> classes, la <xref:System.Text.Json.Serialization.JsonConverterFactory.CreateConverter%2A> méthode a été rendue publique et reçoit un deuxième argument de type <xref:System.Text.Json.JsonSerializerOptions>.</span><span class="sxs-lookup"><span data-stu-id="a8d80-102">To facilitate the composition of <xref:System.Text.Json.Serialization.JsonConverterFactory> classes, the <xref:System.Text.Json.Serialization.JsonConverterFactory.CreateConverter%2A> method has been made public and given a second argument of type <xref:System.Text.Json.JsonSerializerOptions>.</span></span>

#### <a name="details"></a><span data-ttu-id="a8d80-103">Détails</span><span class="sxs-lookup"><span data-stu-id="a8d80-103">Details</span></span>

<span data-ttu-id="a8d80-104">La signature de la `CreateConverter` méthode dans .net Core antérieure à la version 3,0 Preview 8 était la suivante :</span><span class="sxs-lookup"><span data-stu-id="a8d80-104">The signature of the `CreateConverter` method in .NET Core prior to version 3.0 Preview 8 was:</span></span> 

```csharp
namespace System.Text.Json.Serialization
{
    public abstract class JsonConverterFactory : JsonConverter
    {
        protected abstract JsonConverter CreateConverter(Type typeToConvert);
    }
}
```

<span data-ttu-id="a8d80-105">Dans .NET Core 3,0 Preview 8 et versions ultérieures, il s’agit de :</span><span class="sxs-lookup"><span data-stu-id="a8d80-105">In .NET Core 3.0 Preview 8 and later versions, it is:</span></span>

```csharp
namespace System.Text.Json.Serialization
{
    public abstract class JsonConverterFactory : JsonConverter
    {
        public abstract JsonConverter CreateConverter(Type typeToConvert, JsonSerializerOptions options);
    }
}
```

<span data-ttu-id="a8d80-106">Avant cette modification, il était difficile de composer des convertisseurs de fabrique scellés, car il n’existait pas de moyen <xref:System.Text.Json.Serialization.JsonConverter%601> simple de l’en faire.</span><span class="sxs-lookup"><span data-stu-id="a8d80-106">Before this change, it was difficult to compose sealed factory converters, since there was no easy way to get the <xref:System.Text.Json.Serialization.JsonConverter%601> from it.</span></span> <span data-ttu-id="a8d80-107">Rendre la méthode de fabrique publique et transmettre également l' <xref:System.Text.Json.JsonSerializerOptions> autorisation actuelle pour une composition bien plus flexible.</span><span class="sxs-lookup"><span data-stu-id="a8d80-107">Making the factory method public and also passing the current <xref:System.Text.Json.JsonSerializerOptions> allow for much more flexible composition.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="a8d80-108">Version introduite</span><span class="sxs-lookup"><span data-stu-id="a8d80-108">Version introduced</span></span>

<span data-ttu-id="a8d80-109">3,0 Preview 8</span><span class="sxs-lookup"><span data-stu-id="a8d80-109">3.0 Preview 8</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="a8d80-110">Action recommandée</span><span class="sxs-lookup"><span data-stu-id="a8d80-110">Recommended action</span></span>

<span data-ttu-id="a8d80-111">Les classes dérivées doivent être mises à jour et recompilées.</span><span class="sxs-lookup"><span data-stu-id="a8d80-111">Derived classes need to be updated and recompiled.</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="a8d80-112">API affectées</span><span class="sxs-lookup"><span data-stu-id="a8d80-112">Affected APIs</span></span>

<span data-ttu-id="a8d80-113"><xref:System.Text.Json.Serialization.JsonConverterFactory.CreateConverter(System.Type,System.Text.Json.JsonSerializerOptions)?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="a8d80-113"><xref:System.Text.Json.Serialization.JsonConverterFactory.CreateConverter(System.Type,System.Text.Json.JsonSerializerOptions)?displayProperty=nameWithType>.</span></span>

<!-- For tool use only

### Affected APIs

- `M:System.Text.Json.Serialization.JsonConverterFactory.CreateConverter(System.Type,System.Text.Json.JsonSerializerOptions)`

-->
