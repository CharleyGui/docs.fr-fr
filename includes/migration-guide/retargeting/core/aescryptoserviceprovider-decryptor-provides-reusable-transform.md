---
ms.openlocfilehash: 36a9db601f7637185bf48dfcbe2233b4489fcdcf
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85614443"
---
### <a name="aescryptoserviceprovider-decryptor-provides-a-reusable-transform"></a><span data-ttu-id="fd617-101">Le déchiffreur AesCryptoServiceProvider fournit une transformation réutilisable</span><span class="sxs-lookup"><span data-stu-id="fd617-101">AesCryptoServiceProvider decryptor provides a reusable transform</span></span>

#### <a name="details"></a><span data-ttu-id="fd617-102">Détails</span><span class="sxs-lookup"><span data-stu-id="fd617-102">Details</span></span>

<span data-ttu-id="fd617-103">À partir des applications qui ciblent .NET Framework 4.6.2, le déchiffreur <xref:System.Security.Cryptography.AesCryptoServiceProvider> fournit une transformation réutilisable.</span><span class="sxs-lookup"><span data-stu-id="fd617-103">Starting with apps that target the .NET Framework 4.6.2, the <xref:System.Security.Cryptography.AesCryptoServiceProvider> decryptor provides a reusable transform.</span></span> <span data-ttu-id="fd617-104">Après un appel à <xref:System.Security.Cryptography.CryptoAPITransform.TransformFinalBlock(System.Byte[],System.Int32,System.Int32)?displayProperty=fullName>, la transformation est réinitialisée et peut être réutilisée.</span><span class="sxs-lookup"><span data-stu-id="fd617-104">After a call to <xref:System.Security.Cryptography.CryptoAPITransform.TransformFinalBlock(System.Byte[],System.Int32,System.Int32)?displayProperty=fullName>, the transform is reinitialized and can be reused.</span></span> <span data-ttu-id="fd617-105">Pour les applications qui ciblent des versions antérieures du .NET Framework, toute tentative de réutilisation du déchiffreur en appelant <xref:System.Security.Cryptography.CryptoAPITransform.TransformBlock(System.Byte[],System.Int32,System.Int32,System.Byte[],System.Int32)?displayProperty=fullName> après un appel à <xref:System.Security.Cryptography.CryptoAPITransform.TransformFinalBlock(System.Byte[],System.Int32,System.Int32)?displayProperty=fullName> lève un <xref:System.Security.Cryptography.CryptographicException> ou génère des données endommagées.</span><span class="sxs-lookup"><span data-stu-id="fd617-105">For apps that target earlier versions of the .NET Framework, attempting to reuse the decryptor by calling <xref:System.Security.Cryptography.CryptoAPITransform.TransformBlock(System.Byte[],System.Int32,System.Int32,System.Byte[],System.Int32)?displayProperty=fullName> after a call to <xref:System.Security.Cryptography.CryptoAPITransform.TransformFinalBlock(System.Byte[],System.Int32,System.Int32)?displayProperty=fullName> throws a <xref:System.Security.Cryptography.CryptographicException> or produces corrupted data.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="fd617-106">Suggestion</span><span class="sxs-lookup"><span data-stu-id="fd617-106">Suggestion</span></span>

<span data-ttu-id="fd617-107">L’impact de ce changement devrait être minime, car il s’agit du comportement attendu. Les applications qui dépendent du comportement précédent peuvent refuser le changement en ajoutant le paramètre de configuration suivant dans la section `<runtime>` du fichier de configuration de l’application :</span><span class="sxs-lookup"><span data-stu-id="fd617-107">The impact of this change should be minimal, since this is the expected behavior.Applications that depend on the previous behavior can opt out of it using it by adding the following configuration setting to the `<runtime>` section of the application's configuration file:</span></span>

```xml
<runtime>
<AppContextSwitchOverrides value="Switch.System.Security.Cryptography.AesCryptoServiceProvider.DontCorrectlyResetDecryptor=true"/>
</runtime>
```

<span data-ttu-id="fd617-108">De plus, les applications qui ciblent une version antérieure du .NET Framework mais qui s’exécutent dans .NET Framework 4.6.2 ou une version ultérieure peuvent accepter ce changement en ajoutant le paramètre de configuration suivant à la section `<runtime>` du fichier de configuration de l’application :</span><span class="sxs-lookup"><span data-stu-id="fd617-108">In addition, applications that target a previous version of the .NET Framework but are running under a version of the .NET Framework starting with .NET Framework 4.6.2 can opt in to it by adding the following configuration setting to the `<runtime>` section of the application's configuration file:</span></span>

```xml
<runtime>
<AppContextSwitchOverrides value="Switch.System.Security.Cryptography.AesCryptoServiceProvider.DontCorrectlyResetDecryptor=false"/>
</runtime>
```

| <span data-ttu-id="fd617-109">Nom</span><span class="sxs-lookup"><span data-stu-id="fd617-109">Name</span></span>    | <span data-ttu-id="fd617-110">Valeur</span><span class="sxs-lookup"><span data-stu-id="fd617-110">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="fd617-111">Étendue</span><span class="sxs-lookup"><span data-stu-id="fd617-111">Scope</span></span>   | <span data-ttu-id="fd617-112">Secondaire</span><span class="sxs-lookup"><span data-stu-id="fd617-112">Minor</span></span>       |
| <span data-ttu-id="fd617-113">Version</span><span class="sxs-lookup"><span data-stu-id="fd617-113">Version</span></span> | <span data-ttu-id="fd617-114">4.6.2</span><span class="sxs-lookup"><span data-stu-id="fd617-114">4.6.2</span></span>       |
| <span data-ttu-id="fd617-115">Type</span><span class="sxs-lookup"><span data-stu-id="fd617-115">Type</span></span>    | <span data-ttu-id="fd617-116">Reciblage</span><span class="sxs-lookup"><span data-stu-id="fd617-116">Retargeting</span></span> |

#### <a name="affected-apis"></a><span data-ttu-id="fd617-117">API affectées</span><span class="sxs-lookup"><span data-stu-id="fd617-117">Affected APIs</span></span>

- <xref:System.Security.Cryptography.AesCryptoServiceProvider.CreateDecryptor?displayProperty=nameWithType>
