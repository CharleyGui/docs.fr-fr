---
ms.openlocfilehash: 9052f509ec6df4e4b911e2f33b5c8197adb9a2c3
ms.sourcegitcommit: 79a2d6a07ba4ed08979819666a0ee6927bbf1b01
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2019
ms.locfileid: "74568175"
---
### <a name="jsonfactoryconvertercreateconverter-signature-changed"></a><span data-ttu-id="dcd7e-101">Signature de JsonFactoryConverter. CreateConverter modifiée</span><span class="sxs-lookup"><span data-stu-id="dcd7e-101">JsonFactoryConverter.CreateConverter signature changed</span></span>

<span data-ttu-id="dcd7e-102">Pour faciliter la composition des classes <xref:System.Text.Json.Serialization.JsonConverterFactory>, la méthode <xref:System.Text.Json.Serialization.JsonConverterFactory.CreateConverter%2A> a été rendue publique et reçoit un deuxième argument de type <xref:System.Text.Json.JsonSerializerOptions>.</span><span class="sxs-lookup"><span data-stu-id="dcd7e-102">To facilitate the composition of <xref:System.Text.Json.Serialization.JsonConverterFactory> classes, the <xref:System.Text.Json.Serialization.JsonConverterFactory.CreateConverter%2A> method has been made public and given a second argument of type <xref:System.Text.Json.JsonSerializerOptions>.</span></span>

#### <a name="change-description"></a><span data-ttu-id="dcd7e-103">Modifier la description</span><span class="sxs-lookup"><span data-stu-id="dcd7e-103">Change description</span></span>

<span data-ttu-id="dcd7e-104">La signature de la méthode `CreateConverter` dans .NET Core antérieure à la version 3,0 Preview 8 était la suivante :</span><span class="sxs-lookup"><span data-stu-id="dcd7e-104">The signature of the `CreateConverter` method in .NET Core prior to version 3.0 Preview 8 was:</span></span>

```csharp
namespace System.Text.Json.Serialization
{
    public abstract class JsonConverterFactory : JsonConverter
    {
        protected abstract JsonConverter CreateConverter(Type typeToConvert);
    }
}
```

<span data-ttu-id="dcd7e-105">Dans .NET Core 3,0 Preview 8 et versions ultérieures, il s’agit de :</span><span class="sxs-lookup"><span data-stu-id="dcd7e-105">In .NET Core 3.0 Preview 8 and later versions, it is:</span></span>

```csharp
namespace System.Text.Json.Serialization
{
    public abstract class JsonConverterFactory : JsonConverter
    {
        public abstract JsonConverter CreateConverter(Type typeToConvert, JsonSerializerOptions options);
    }
}
```

<span data-ttu-id="dcd7e-106">Avant cette modification, il était difficile de composer des convertisseurs de fabrique scellés, car il n’existait pas de moyen facile d’y <xref:System.Text.Json.Serialization.JsonConverter%601> parvenir.</span><span class="sxs-lookup"><span data-stu-id="dcd7e-106">Before this change, it was difficult to compose sealed factory converters, since there was no easy way to get the <xref:System.Text.Json.Serialization.JsonConverter%601> from it.</span></span> <span data-ttu-id="dcd7e-107">Rendre la méthode de fabrique publique et transmettre également le <xref:System.Text.Json.JsonSerializerOptions> actuel permet une composition bien plus flexible.</span><span class="sxs-lookup"><span data-stu-id="dcd7e-107">Making the factory method public and also passing the current <xref:System.Text.Json.JsonSerializerOptions> allow for much more flexible composition.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="dcd7e-108">Version introduite</span><span class="sxs-lookup"><span data-stu-id="dcd7e-108">Version introduced</span></span>

<span data-ttu-id="dcd7e-109">3,0 Preview 8</span><span class="sxs-lookup"><span data-stu-id="dcd7e-109">3.0 Preview 8</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="dcd7e-110">Action recommandée</span><span class="sxs-lookup"><span data-stu-id="dcd7e-110">Recommended action</span></span>

<span data-ttu-id="dcd7e-111">Les classes dérivées doivent être mises à jour et recompilées.</span><span class="sxs-lookup"><span data-stu-id="dcd7e-111">Derived classes need to be updated and recompiled.</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="dcd7e-112">API affectées</span><span class="sxs-lookup"><span data-stu-id="dcd7e-112">Affected APIs</span></span>

<span data-ttu-id="dcd7e-113"><xref:System.Text.Json.Serialization.JsonConverterFactory.CreateConverter(System.Type,System.Text.Json.JsonSerializerOptions)?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="dcd7e-113"><xref:System.Text.Json.Serialization.JsonConverterFactory.CreateConverter(System.Type,System.Text.Json.JsonSerializerOptions)?displayProperty=nameWithType>.</span></span>

<!-- For tool use only

### Affected APIs

- `M:System.Text.Json.Serialization.JsonConverterFactory.CreateConverter(System.Type,System.Text.Json.JsonSerializerOptions)`

-->
