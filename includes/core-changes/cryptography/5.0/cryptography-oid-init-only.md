---
ms.openlocfilehash: cf51d5f6b3eee7189fd9613b3d780a829d197a04
ms.sourcegitcommit: 8bfeb5930ca48b2ee6053f16082dcaf24d46d221
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/18/2020
ms.locfileid: "88558000"
---
### <a name="systemsecuritycryptographyoid-is-functionally-init-only"></a><span data-ttu-id="19edb-101">System. Security. Cryptography. OID est fonctionnellement init-only</span><span class="sxs-lookup"><span data-stu-id="19edb-101">System.Security.Cryptography.Oid is functionally init-only</span></span>

<span data-ttu-id="19edb-102">La <xref:System.Security.Cryptography.Oid?displayProperty=fullName> classe, qui est utilisée pour représenter les valeurs de l’identificateur d’objet ASN. 1 et leurs noms « conviviaux », était auparavant complètement mutable.</span><span class="sxs-lookup"><span data-stu-id="19edb-102">The <xref:System.Security.Cryptography.Oid?displayProperty=fullName> class, which is used to represent ASN.1 Object Identifier values and their "friendly" names, was previously fully mutable.</span></span> <span data-ttu-id="19edb-103">Cette mutabilité a souvent été négligée ou est apparue comme une surprise.</span><span class="sxs-lookup"><span data-stu-id="19edb-103">This mutability was often overlooked or came as a surprise.</span></span> <span data-ttu-id="19edb-104">Les accesseurs set de propriété lèvent désormais une <xref:System.PlatformNotSupportedException> lorsque vous tentez de modifier la valeur une fois qu’elle a déjà été assignée.</span><span class="sxs-lookup"><span data-stu-id="19edb-104">The property setters now throw a <xref:System.PlatformNotSupportedException> when you attempt to change the value after it's already been assigned.</span></span>

#### <a name="change-description"></a><span data-ttu-id="19edb-105">Description de la modification</span><span class="sxs-lookup"><span data-stu-id="19edb-105">Change description</span></span>

<span data-ttu-id="19edb-106">Dans les versions précédentes, les accesseurs set de propriété on <xref:System.Security.Cryptography.Oid> peuvent être utilisés pour modifier la valeur des <xref:System.Security.Cryptography.Oid.FriendlyName> <xref:System.Security.Cryptography.Oid.Value> Propriétés et.</span><span class="sxs-lookup"><span data-stu-id="19edb-106">In previous versions, the property setters on <xref:System.Security.Cryptography.Oid> can be used to change the value of the <xref:System.Security.Cryptography.Oid.FriendlyName> and <xref:System.Security.Cryptography.Oid.Value> properties.</span></span>

<span data-ttu-id="19edb-107">Dans .NET 5,0 et versions ultérieures, les accesseurs set de propriété ne peuvent être utilisés que pour initialiser la valeur.</span><span class="sxs-lookup"><span data-stu-id="19edb-107">In .NET 5.0 and later versions, the property setters can only be used to initialize the value.</span></span> <span data-ttu-id="19edb-108">Une fois que la propriété a une valeur, qu’il s’agisse d’un constructeur ou d’un appel précédent à la méthode setter de propriété, la méthode setter de la propriété lève toujours une exception <xref:System.PlatformNotSupportedException> .</span><span class="sxs-lookup"><span data-stu-id="19edb-108">Once the property has a value, either from a constructor or a previous call to the property setter, the property setter always throws a <xref:System.PlatformNotSupportedException>.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="19edb-109">Motif de modification</span><span class="sxs-lookup"><span data-stu-id="19edb-109">Reason for change</span></span>

<span data-ttu-id="19edb-110">Cette modification permet de réutiliser des <xref:System.Security.Cryptography.Oid> objets dans le cadre de valeurs de retour dans les API publiques pour réduire les profils d’allocation d’objets.</span><span class="sxs-lookup"><span data-stu-id="19edb-110">This change enables the reuse of <xref:System.Security.Cryptography.Oid> objects as part of return values in public APIs to reduce object allocation profiles.</span></span> <span data-ttu-id="19edb-111">Cela évite d’avoir à créer des copies « défensives » temporaires lorsque les <xref:System.Security.Cryptography.Oid> valeurs sont utilisées comme entrées.</span><span class="sxs-lookup"><span data-stu-id="19edb-111">It avoids the need to create temporary "defensive" copies when <xref:System.Security.Cryptography.Oid> values are used as inputs.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="19edb-112">Version introduite</span><span class="sxs-lookup"><span data-stu-id="19edb-112">Version introduced</span></span>

<span data-ttu-id="19edb-113">5,0 Preview 8</span><span class="sxs-lookup"><span data-stu-id="19edb-113">5.0 Preview 8</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="19edb-114">Action recommandée</span><span class="sxs-lookup"><span data-stu-id="19edb-114">Recommended action</span></span>

<span data-ttu-id="19edb-115">Évitez d’utiliser les <xref:System.Security.Cryptography.Oid> accesseurs set de propriété autres que pour l’initialisation d’objet.</span><span class="sxs-lookup"><span data-stu-id="19edb-115">Avoid using the <xref:System.Security.Cryptography.Oid> property setters other than for object initialization.</span></span> <span data-ttu-id="19edb-116">Pour représenter une nouvelle valeur, utilisez une nouvelle instance au lieu de modifier la valeur d’un objet existant.</span><span class="sxs-lookup"><span data-stu-id="19edb-116">To represent a new value, use a new instance instead of changing the value on an existing object.</span></span>

#### <a name="category"></a><span data-ttu-id="19edb-117">Category</span><span class="sxs-lookup"><span data-stu-id="19edb-117">Category</span></span>

<span data-ttu-id="19edb-118">Chiffrement</span><span class="sxs-lookup"><span data-stu-id="19edb-118">Cryptography</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="19edb-119">API affectées</span><span class="sxs-lookup"><span data-stu-id="19edb-119">Affected APIs</span></span>

- <xref:System.Security.Cryptography.Oid.FriendlyName?displayProperty=fullName>
- <xref:System.Security.Cryptography.Oid.Value?displayProperty=fullName>

<!--

#### Affected APIs

- `P:System.Security.Cryptography.Oid.FriendlyName`
- `P:System.Security.Cryptography.Oid.Value`

-->
