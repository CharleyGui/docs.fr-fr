---
title: 'Modification avec rupture : Cryptography. OID est fonctionnellement init-only'
description: En savoir plus sur la modification avec rupture dans .NET 5,0 où les accesseurs set de propriété sur la classe Cryptography. OID lèvent désormais une exception si vous tentez de modifier une valeur.
ms.date: 08/16/2020
ms.openlocfilehash: a3b5a393e2a84f7c9a60c2a821ecfda9c6acd2e3
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95760884"
---
# <a name="systemsecuritycryptographyoid-is-functionally-init-only"></a><span data-ttu-id="9d104-103">System. Security. Cryptography. OID est fonctionnellement init-only</span><span class="sxs-lookup"><span data-stu-id="9d104-103">System.Security.Cryptography.Oid is functionally init-only</span></span>

<span data-ttu-id="9d104-104">La <xref:System.Security.Cryptography.Oid?displayProperty=fullName> classe, qui est utilisée pour représenter les valeurs de l’identificateur d’objet ASN. 1 et leurs noms « conviviaux », était auparavant complètement mutable.</span><span class="sxs-lookup"><span data-stu-id="9d104-104">The <xref:System.Security.Cryptography.Oid?displayProperty=fullName> class, which is used to represent ASN.1 Object Identifier values and their "friendly" names, was previously fully mutable.</span></span> <span data-ttu-id="9d104-105">Cette mutabilité a souvent été négligée ou est apparue comme une surprise.</span><span class="sxs-lookup"><span data-stu-id="9d104-105">This mutability was often overlooked or came as a surprise.</span></span> <span data-ttu-id="9d104-106">Les accesseurs set de propriété lèvent désormais une <xref:System.PlatformNotSupportedException> lorsque vous tentez de modifier la valeur une fois qu’elle a déjà été assignée.</span><span class="sxs-lookup"><span data-stu-id="9d104-106">The property setters now throw a <xref:System.PlatformNotSupportedException> when you attempt to change the value after it's already been assigned.</span></span>

## <a name="change-description"></a><span data-ttu-id="9d104-107">Description de la modification</span><span class="sxs-lookup"><span data-stu-id="9d104-107">Change description</span></span>

<span data-ttu-id="9d104-108">Dans les versions précédentes, les accesseurs set de propriété on <xref:System.Security.Cryptography.Oid> peuvent être utilisés pour modifier la valeur des <xref:System.Security.Cryptography.Oid.FriendlyName> <xref:System.Security.Cryptography.Oid.Value> Propriétés et.</span><span class="sxs-lookup"><span data-stu-id="9d104-108">In previous versions, the property setters on <xref:System.Security.Cryptography.Oid> can be used to change the value of the <xref:System.Security.Cryptography.Oid.FriendlyName> and <xref:System.Security.Cryptography.Oid.Value> properties.</span></span>

<span data-ttu-id="9d104-109">Dans .NET 5,0 et versions ultérieures, les accesseurs set de propriété ne peuvent être utilisés que pour initialiser la valeur.</span><span class="sxs-lookup"><span data-stu-id="9d104-109">In .NET 5.0 and later versions, the property setters can only be used to initialize the value.</span></span> <span data-ttu-id="9d104-110">Une fois que la propriété a une valeur, qu’il s’agisse d’un constructeur ou d’un appel précédent à la méthode setter de propriété, la méthode setter de la propriété lève toujours une exception <xref:System.PlatformNotSupportedException> .</span><span class="sxs-lookup"><span data-stu-id="9d104-110">Once the property has a value, either from a constructor or a previous call to the property setter, the property setter always throws a <xref:System.PlatformNotSupportedException>.</span></span>

## <a name="reason-for-change"></a><span data-ttu-id="9d104-111">Motif de modification</span><span class="sxs-lookup"><span data-stu-id="9d104-111">Reason for change</span></span>

<span data-ttu-id="9d104-112">Cette modification permet de réutiliser des <xref:System.Security.Cryptography.Oid> objets dans le cadre de valeurs de retour dans les API publiques pour réduire les profils d’allocation d’objets.</span><span class="sxs-lookup"><span data-stu-id="9d104-112">This change enables the reuse of <xref:System.Security.Cryptography.Oid> objects as part of return values in public APIs to reduce object allocation profiles.</span></span> <span data-ttu-id="9d104-113">Cela évite d’avoir à créer des copies « défensives » temporaires lorsque les <xref:System.Security.Cryptography.Oid> valeurs sont utilisées comme entrées.</span><span class="sxs-lookup"><span data-stu-id="9d104-113">It avoids the need to create temporary "defensive" copies when <xref:System.Security.Cryptography.Oid> values are used as inputs.</span></span>

## <a name="version-introduced"></a><span data-ttu-id="9d104-114">Version introduite</span><span class="sxs-lookup"><span data-stu-id="9d104-114">Version introduced</span></span>

<span data-ttu-id="9d104-115">5.0</span><span class="sxs-lookup"><span data-stu-id="9d104-115">5.0</span></span>

## <a name="recommended-action"></a><span data-ttu-id="9d104-116">Action recommandée</span><span class="sxs-lookup"><span data-stu-id="9d104-116">Recommended action</span></span>

<span data-ttu-id="9d104-117">Évitez d’utiliser les <xref:System.Security.Cryptography.Oid> accesseurs set de propriété autres que pour l’initialisation d’objet.</span><span class="sxs-lookup"><span data-stu-id="9d104-117">Avoid using the <xref:System.Security.Cryptography.Oid> property setters other than for object initialization.</span></span> <span data-ttu-id="9d104-118">Pour représenter une nouvelle valeur, utilisez une nouvelle instance au lieu de modifier la valeur d’un objet existant.</span><span class="sxs-lookup"><span data-stu-id="9d104-118">To represent a new value, use a new instance instead of changing the value on an existing object.</span></span>

## <a name="affected-apis"></a><span data-ttu-id="9d104-119">API affectées</span><span class="sxs-lookup"><span data-stu-id="9d104-119">Affected APIs</span></span>

- <xref:System.Security.Cryptography.Oid.FriendlyName?displayProperty=fullName>
- <xref:System.Security.Cryptography.Oid.Value?displayProperty=fullName>

<!--

### Affected APIs

- `P:System.Security.Cryptography.Oid.FriendlyName`
- `P:System.Security.Cryptography.Oid.Value`

### Category

Cryptography

-->
