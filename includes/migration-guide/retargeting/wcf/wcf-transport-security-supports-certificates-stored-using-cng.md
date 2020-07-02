---
ms.openlocfilehash: 5c09bee92f679cd7e7a95cd23d5ce0ca9b57170c
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85614499"
---
### <a name="wcf-transport-security-supports-certificates-stored-using-cng"></a><span data-ttu-id="da87a-101">La sécurité du transport WCF prend en charge les certificats stockés à l’aide de CNG</span><span class="sxs-lookup"><span data-stu-id="da87a-101">WCF transport security supports certificates stored using CNG</span></span>

#### <a name="details"></a><span data-ttu-id="da87a-102">Détails</span><span class="sxs-lookup"><span data-stu-id="da87a-102">Details</span></span>

<span data-ttu-id="da87a-103">À partir des applications qui ciblent .NET Framework 4.6.2, la sécurité du transport WCF prend en charge les certificats stockés à l’aide de la bibliothèque de chiffrement Windows (CNG).</span><span class="sxs-lookup"><span data-stu-id="da87a-103">Starting with apps that target the .NET Framework 4.6.2, WCF transport security supports certificates stored using the Windows Cryptography Library (CNG).</span></span> <span data-ttu-id="da87a-104">Cette prise en charge se limite aux certificats avec une clé publique dont l’exposant ne dépasse pas 32 bits de longueur.</span><span class="sxs-lookup"><span data-stu-id="da87a-104">This support is limited to certificates with a public key that has an exponent no more than 32 bits in length.</span></span> <span data-ttu-id="da87a-105">Quand une application cible .NET Framework 4.6.2, cette fonctionnalité est activée par défaut. Dans les versions antérieures du .NET Framework, les tentatives d’utilisation de certificats X509 avec un fournisseur de stockage de clés CSG lèvent une exception.</span><span class="sxs-lookup"><span data-stu-id="da87a-105">When an application targets the .NET Framework 4.6.2, this feature is on by default.In earlier versions of the .NET Framework, the attempt to use X509 certificates with a CSG key storage provider throws an exception.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="da87a-106">Suggestion</span><span class="sxs-lookup"><span data-stu-id="da87a-106">Suggestion</span></span>

<span data-ttu-id="da87a-107">Les applications qui ciblent .NET Framework 4.6.1 et les versions antérieures mais qui s’exécutent sur .NET Framework 4.6.2 peuvent activer la prise en charge des certificats CNG en ajoutant la ligne suivante à la section `<runtime>` du fichier app.config ou web.config :</span><span class="sxs-lookup"><span data-stu-id="da87a-107">Apps that target the .NET Framework 4.6.1 and earlier but are running on the .NET Framework 4.6.2 can enable support for CNG certificates by adding the following line to the `<runtime>` section of the app.config or web.config file:</span></span>

```xml
<runtime>
  <AppContextSwitchOverrides value="Switch.System.ServiceModel.DisableCngCertificates=false" />
</runtime>
```

<span data-ttu-id="da87a-108">Vous pouvez en faire autant par programmation avec un code de ce type :</span><span class="sxs-lookup"><span data-stu-id="da87a-108">This can also be done programmatically with the following code:</span></span>

```csharp
private const string DisableCngCertificates = @"Switch.System.ServiceModel.DisableCngCertificate";

AppContext.SetSwitch(disableCngCertificates, false);
```

```vb
Const DisableCngCertificates As String = "Switch.System.ServiceModel.DisableCngCertificates"
AppContext.SetSwitch(disableCngCertificates, False)
```

<span data-ttu-id="da87a-109">Notez qu’en raison de cette modification, tout code de traitement des exceptions qui dépend de l’échec de la tentative d’établissement d’une communication sécurisée avec un certificat CNG ne s’exécutera plus.</span><span class="sxs-lookup"><span data-stu-id="da87a-109">Note that, because of this change, any exception handling code that depends on the attempt to initiate secure communication with a CNG certificate to fail will no longer execute.</span></span>

| <span data-ttu-id="da87a-110">Nom</span><span class="sxs-lookup"><span data-stu-id="da87a-110">Name</span></span>    | <span data-ttu-id="da87a-111">Valeur</span><span class="sxs-lookup"><span data-stu-id="da87a-111">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="da87a-112">Étendue</span><span class="sxs-lookup"><span data-stu-id="da87a-112">Scope</span></span>   | <span data-ttu-id="da87a-113">Secondaire</span><span class="sxs-lookup"><span data-stu-id="da87a-113">Minor</span></span>       |
| <span data-ttu-id="da87a-114">Version</span><span class="sxs-lookup"><span data-stu-id="da87a-114">Version</span></span> | <span data-ttu-id="da87a-115">4.6.2</span><span class="sxs-lookup"><span data-stu-id="da87a-115">4.6.2</span></span>       |
| <span data-ttu-id="da87a-116">Type</span><span class="sxs-lookup"><span data-stu-id="da87a-116">Type</span></span>    | <span data-ttu-id="da87a-117">Reciblage</span><span class="sxs-lookup"><span data-stu-id="da87a-117">Retargeting</span></span> |
