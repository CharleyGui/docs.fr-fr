---
ms.openlocfilehash: 5083403a24a4a695d6970ef9c7a006796f41a86b
ms.sourcegitcommit: 97405ed212f69b0a32faa66a5d5fae7e76628b68
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2020
ms.locfileid: "91609294"
---
### <a name="mvc-objectmodelvalidator-calls-a-new-overload-of-validationvisitorvalidate"></a><span data-ttu-id="d15c6-101">MVC : ObjectModelValidator appelle une nouvelle surcharge de ValidationVisitor. Validate</span><span class="sxs-lookup"><span data-stu-id="d15c6-101">MVC: ObjectModelValidator calls a new overload of ValidationVisitor.Validate</span></span>

<span data-ttu-id="d15c6-102">Dans ASP.NET Core 5,0, une surcharge du <xref:Microsoft.AspNetCore.Mvc.ModelBinding.Validation.ValidationVisitor.Validate%2A?displayProperty=nameWithType> a été ajoutée.</span><span class="sxs-lookup"><span data-stu-id="d15c6-102">In ASP.NET Core 5.0, an overload of the <xref:Microsoft.AspNetCore.Mvc.ModelBinding.Validation.ValidationVisitor.Validate%2A?displayProperty=nameWithType> was added.</span></span> <span data-ttu-id="d15c6-103">La nouvelle surcharge accepte l’instance de modèle de niveau supérieur qui contient des propriétés :</span><span class="sxs-lookup"><span data-stu-id="d15c6-103">The new overload accepts the top-level model instance that contains properties:</span></span>

```diff
  bool Validate(ModelMetadata metadata, string key, object model, bool alwaysValidateAtTopLevel);
+ bool Validate(ModelMetadata metadata, string key, object model, bool alwaysValidateAtTopLevel, object container);
```

<span data-ttu-id="d15c6-104"><xref:Microsoft.AspNetCore.Mvc.ModelBinding.ObjectModelValidator> appelle cette nouvelle surcharge de `ValidationVisitor` pour effectuer la validation.</span><span class="sxs-lookup"><span data-stu-id="d15c6-104"><xref:Microsoft.AspNetCore.Mvc.ModelBinding.ObjectModelValidator> invokes this new overload of `ValidationVisitor` to perform validation.</span></span> <span data-ttu-id="d15c6-105">Cette nouvelle surcharge est utile si votre bibliothèque de validation s’intègre au système de validation de modèle de ASP.NET Core MVC.</span><span class="sxs-lookup"><span data-stu-id="d15c6-105">This new overload is pertinent if your validation library integrates with ASP.NET Core MVC's model validation system.</span></span>

<span data-ttu-id="d15c6-106">Pour plus d’informations, consultez GitHub issue [dotnet/aspnetcore # 26020](https://github.com/dotnet/aspnetcore/issues/26020).</span><span class="sxs-lookup"><span data-stu-id="d15c6-106">For discussion, see GitHub issue [dotnet/aspnetcore#26020](https://github.com/dotnet/aspnetcore/issues/26020).</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="d15c6-107">Version introduite</span><span class="sxs-lookup"><span data-stu-id="d15c6-107">Version introduced</span></span>

<span data-ttu-id="d15c6-108">5.0</span><span class="sxs-lookup"><span data-stu-id="d15c6-108">5.0</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="d15c6-109">Ancien comportement</span><span class="sxs-lookup"><span data-stu-id="d15c6-109">Old behavior</span></span>

<span data-ttu-id="d15c6-110">`ObjectModelValidator` appelle la surcharge suivante pendant la validation du modèle :</span><span class="sxs-lookup"><span data-stu-id="d15c6-110">`ObjectModelValidator` invokes the following overload during model validation:</span></span>

```csharp
ValidationVisitor.Validate(ModelMetadata metadata, string key, object model, bool alwaysValidateAtTopLevel)
```

#### <a name="new-behavior"></a><span data-ttu-id="d15c6-111">Nouveau comportement</span><span class="sxs-lookup"><span data-stu-id="d15c6-111">New behavior</span></span>

<span data-ttu-id="d15c6-112">`ObjectModelValidator` appelle la surcharge suivante pendant la validation du modèle :</span><span class="sxs-lookup"><span data-stu-id="d15c6-112">`ObjectModelValidator` invokes the following overload during model validation:</span></span>

```csharp
ValidationVisitor.Validate(ModelMetadata metadata, string key, object model, bool alwaysValidateAtTopLevel, object container)
```

#### <a name="reason-for-change"></a><span data-ttu-id="d15c6-113">Motif de modification</span><span class="sxs-lookup"><span data-stu-id="d15c6-113">Reason for change</span></span>

<span data-ttu-id="d15c6-114">Cette modification a été introduite pour prendre en charge les validateurs, tels que <xref:System.ComponentModel.DataAnnotations.CompareAttribute> , qui reposent sur l’inspection d’autres propriétés.</span><span class="sxs-lookup"><span data-stu-id="d15c6-114">This change was introduced to support validators, such as <xref:System.ComponentModel.DataAnnotations.CompareAttribute>, that rely on inspection of other properties.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="d15c6-115">Action recommandée</span><span class="sxs-lookup"><span data-stu-id="d15c6-115">Recommended action</span></span>

<span data-ttu-id="d15c6-116">Les infrastructures de validation qui reposent sur `ObjectModelValidator` pour appeler la surcharge existante de `ValidationVisitor` doivent substituer la nouvelle méthode quand vous ciblez .net 5,0 ou une version ultérieure :</span><span class="sxs-lookup"><span data-stu-id="d15c6-116">Validation frameworks that rely on `ObjectModelValidator` to invoke the existing overload of `ValidationVisitor` must override the new method when targeting .NET 5.0 or later:</span></span>

```csharp
public class MyCustomValidationVisitor : ValidationVisitor
{
+  public override bool Validate(ModelMetadata metadata, string key, object model, bool alwaysValidateAtTopLevel, object container)
+  {
+    ...
}
```

#### <a name="category"></a><span data-ttu-id="d15c6-117">Category</span><span class="sxs-lookup"><span data-stu-id="d15c6-117">Category</span></span>

<span data-ttu-id="d15c6-118">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="d15c6-118">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="d15c6-119">API affectées</span><span class="sxs-lookup"><span data-stu-id="d15c6-119">Affected APIs</span></span>

<xref:Microsoft.AspNetCore.Mvc.ModelBinding.Validation.ValidationVisitor.Validate%2A?displayProperty=nameWithType>

<!--

#### Affected APIs

`Overload:Microsoft.AspNetCore.Mvc.ModelBinding.Validation.ValidationVisitor.Validate`

-->
