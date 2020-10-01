---
ms.openlocfilehash: 5083403a24a4a695d6970ef9c7a006796f41a86b
ms.sourcegitcommit: 97405ed212f69b0a32faa66a5d5fae7e76628b68
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2020
ms.locfileid: "91609294"
---
### <a name="mvc-objectmodelvalidator-calls-a-new-overload-of-validationvisitorvalidate"></a>MVC : ObjectModelValidator appelle une nouvelle surcharge de ValidationVisitor. Validate

Dans ASP.NET Core 5,0, une surcharge du <xref:Microsoft.AspNetCore.Mvc.ModelBinding.Validation.ValidationVisitor.Validate%2A?displayProperty=nameWithType> a été ajoutée. La nouvelle surcharge accepte l’instance de modèle de niveau supérieur qui contient des propriétés :

```diff
  bool Validate(ModelMetadata metadata, string key, object model, bool alwaysValidateAtTopLevel);
+ bool Validate(ModelMetadata metadata, string key, object model, bool alwaysValidateAtTopLevel, object container);
```

<xref:Microsoft.AspNetCore.Mvc.ModelBinding.ObjectModelValidator> appelle cette nouvelle surcharge de `ValidationVisitor` pour effectuer la validation. Cette nouvelle surcharge est utile si votre bibliothèque de validation s’intègre au système de validation de modèle de ASP.NET Core MVC.

Pour plus d’informations, consultez GitHub issue [dotnet/aspnetcore # 26020](https://github.com/dotnet/aspnetcore/issues/26020).

#### <a name="version-introduced"></a>Version introduite

5.0

#### <a name="old-behavior"></a>Ancien comportement

`ObjectModelValidator` appelle la surcharge suivante pendant la validation du modèle :

```csharp
ValidationVisitor.Validate(ModelMetadata metadata, string key, object model, bool alwaysValidateAtTopLevel)
```

#### <a name="new-behavior"></a>Nouveau comportement

`ObjectModelValidator` appelle la surcharge suivante pendant la validation du modèle :

```csharp
ValidationVisitor.Validate(ModelMetadata metadata, string key, object model, bool alwaysValidateAtTopLevel, object container)
```

#### <a name="reason-for-change"></a>Motif de modification

Cette modification a été introduite pour prendre en charge les validateurs, tels que <xref:System.ComponentModel.DataAnnotations.CompareAttribute> , qui reposent sur l’inspection d’autres propriétés.

#### <a name="recommended-action"></a>Action recommandée

Les infrastructures de validation qui reposent sur `ObjectModelValidator` pour appeler la surcharge existante de `ValidationVisitor` doivent substituer la nouvelle méthode quand vous ciblez .net 5,0 ou une version ultérieure :

```csharp
public class MyCustomValidationVisitor : ValidationVisitor
{
+  public override bool Validate(ModelMetadata metadata, string key, object model, bool alwaysValidateAtTopLevel, object container)
+  {
+    ...
}
```

#### <a name="category"></a>Category

ASP.NET Core

#### <a name="affected-apis"></a>API affectées

<xref:Microsoft.AspNetCore.Mvc.ModelBinding.Validation.ValidationVisitor.Validate%2A?displayProperty=nameWithType>

<!--

#### Affected APIs

`Overload:Microsoft.AspNetCore.Mvc.ModelBinding.Validation.ValidationVisitor.Validate`

-->
