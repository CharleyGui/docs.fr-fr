---
ms.openlocfilehash: d8506893f5b3eefa6f46dc9f773e43b125ee5210
ms.sourcegitcommit: e48a54ebe62e874500a7043f6ee0b77a744d55b4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/26/2020
ms.locfileid: "80291641"
---
### <a name="azure-microsoft-prefixed-azure-integration-packages-removed"></a>Azure : Les paquets d’intégration Azure préfixés de Microsoft supprimés

Les `Microsoft.*` paquets suivants qui assurent l’intégration entre ASP.NET Core et Azure SDKs ne sont pas inclus dans ASP.NET Core 5.0 :

* [Microsoft.Extensions.Configuration.AzureKeyVault](https://www.nuget.org/packages/Microsoft.Extensions.Configuration.AzureKeyVault/), qui intègre [Azure Key Vault](/azure/key-vault/) dans le [système Configuration](/aspnet/core/fundamentals/configuration/).
* [Microsoft.AspNetCore.DataProtection.AzureKeyVault](https://www.nuget.org/packages/Microsoft.AspNetCore.DataProtection.AzureKeyVault/), qui intègre Azure Key Vault dans le [système ASP.NET Core Data Protection](/aspnet/core/security/data-protection/introduction).
* [Microsoft.AspNetCore.DataProtection.AzureStorage](https://www.nuget.org/packages/Microsoft.AspNetCore.DataProtection.AzureStorage/), qui intègre [Azure Blob Storage](/azure/storage/blobs/) dans le système ASP.NET Core Data Protection.

Pour discussion sur cette question, voir [dotnet/aspnetcore-19570](https://github.com/dotnet/aspnetcore/issues/19570).

#### <a name="version-introduced"></a>Version introduite

5.0 Aperçu 1

#### <a name="old-behavior"></a>Ancien comportement

Les `Microsoft.*` forfaits intègrent les services Azure avec les API Configuration et Protection des Données.

#### <a name="new-behavior"></a>Nouveau comportement

De `Azure.*` nouveaux forfaits intègrent les services Azure aux API Configuration et Protection des Données.

#### <a name="reason-for-change"></a>Raison du changement

Le changement a `Microsoft.*` été apporté parce que les paquets étaient :

* Utilisation de versions désuètes de l’Azure SDK. Des mises à jour simples n’étaient pas possibles car les nouvelles versions de l’Azure SDK incluaient des modifications de rupture.
* Lié à l’horaire de sortie .NET Core. Le transfert de la propriété des paquets à l’équipe Azure SDK permet de mettre à jour les paquets au fur et à mesure que le SDK Azure est mis à jour.

#### <a name="recommended-action"></a>Action recommandée

Dans ASP.NET Projets Core 2.1 ou plus `Microsoft.*` tard, `Azure.*` remplacez l’ancien par les nouveaux paquets.

| Vieux | Nouveau |
|--|--|
| `Microsoft.AspNetCore.DataProtection.AzureKeyVault` | [Azure.AspNetCore.DataProtection.Keys Azure.AspNetCore.DataProtection.Keys Azure.AspNetCore.DataProtection.Keys Azure](https://www.nuget.org/packages/Azure.AspNetCore.DataProtection.Keys) |
| `Microsoft.AspNetCore.DataProtection.AzureStorage` | [Azure.AspNetCore.DataProtection.Blobs Azure.AspNetCore.DataProtection.Blobs Azure.AspNetCore.DataProtection.Blobs Azure](https://www.nuget.org/packages/Azure.AspNetCore.DataProtection.Blobs) |
| `Microsoft.Extensions.Configuration.AzureKeyVault` | [Azure.Extensions.Configuration.Secrets Azure.Extensions.Configuration.Secrets Azure.Extensions.Configuration.Secrets Azure](https://www.nuget.org/packages/Azure.Extensions.Configuration.Secrets) |

Les nouveaux paquets utilisent une nouvelle version de l’Azure SDK qui comprend des changements de rupture. Les habitudes générales d’utilisation sont inchangées. Certaines surcharges et options peuvent différer pour s’adapter aux changements des API azure SDK sous-jacentes.

Les anciens paquets seront:

* Soyez soutenu par l’équipe ASP.NET Core pour la durée de vie de .NET Core 2.1 et 3.1.
* Ne pas être inclus dans .NET 5.

Lors de la mise à niveau de `Azure.*` votre projet à .NET 5, passez aux paquets pour maintenir le soutien.

#### <a name="category"></a>Category

ASP.NET Core

#### <a name="affected-apis"></a>API affectées

- <xref:Microsoft.Extensions.Configuration.AzureKeyVaultConfigurationExtensions.AddAzureKeyVault%2A?displayProperty=nameWithType>
- <xref:Microsoft.AspNetCore.DataProtection.AzureDataProtectionBuilderExtensions.ProtectKeysWithAzureKeyVault%2A?displayProperty=nameWithType>
- <xref:Microsoft.AspNetCore.DataProtection.AzureDataProtectionBuilderExtensions.PersistKeysToAzureBlobStorage%2A?displayProperty=nameWithType>

<!--

#### Affected APIs

- `Overload:Microsoft.Extensions.Configuration.AzureKeyVaultConfigurationExtensions.AddAzureKeyVault`
- `Overload:Microsoft.AspNetCore.DataProtection.AzureDataProtectionBuilderExtensions.ProtectKeysWithAzureKeyVault`
- `Overload:Microsoft.AspNetCore.DataProtection.AzureDataProtectionBuilderExtensions.PersistKeysToAzureBlobStorage`

-->
