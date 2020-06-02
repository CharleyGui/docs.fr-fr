---
title: Conception de champs
ms.date: 10/22/2008
ms.technology: dotnet-standard
helpviewer_keywords:
- fields, design guidelines
- read-only fields
- member design guidelines, fields
ms.assetid: 7cb4b0f3-7a10-4c93-b84d-733f7134fcf8
ms.openlocfilehash: 3a5ae985ab161899fbb5e96f9b0ef0cfa90b957c
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/02/2020
ms.locfileid: "84289744"
---
# <a name="field-design"></a><span data-ttu-id="f5044-102">Conception de champs</span><span class="sxs-lookup"><span data-stu-id="f5044-102">Field Design</span></span>
<span data-ttu-id="f5044-103">Le principe de l’encapsulation est l’une des notions les plus importantes en matière de conception orientée objet.</span><span class="sxs-lookup"><span data-stu-id="f5044-103">The principle of encapsulation is one of the most important notions in object-oriented design.</span></span> <span data-ttu-id="f5044-104">Ce principe stipule que les données stockées dans un objet ne doivent être accessibles qu’à cet objet.</span><span class="sxs-lookup"><span data-stu-id="f5044-104">This principle states that data stored inside an object should be accessible only to that object.</span></span>

 <span data-ttu-id="f5044-105">Une méthode utile pour interpréter le principe consiste à indiquer qu’un type doit être conçu de manière à ce que les modifications apportées aux champs de ce type (modification de nom ou de type) puissent être effectuées sans interrompre le code autre que pour les membres du type.</span><span class="sxs-lookup"><span data-stu-id="f5044-105">A useful way to interpret the principle is to say that a type should be designed so that changes to fields of that type (name or type changes) can be made without breaking code other than for members of the type.</span></span> <span data-ttu-id="f5044-106">Cette interprétation implique immédiatement que tous les champs doivent être privés.</span><span class="sxs-lookup"><span data-stu-id="f5044-106">This interpretation immediately implies that all fields must be private.</span></span>

 <span data-ttu-id="f5044-107">Nous excluons les champs constants et statiques en lecture seule de cette restriction stricte, car ces champs, presque par définition, ne sont jamais requis pour la modification.</span><span class="sxs-lookup"><span data-stu-id="f5044-107">We exclude constant and static read-only fields from this strict restriction, because such fields, almost by definition, are never required to change.</span></span>

 <span data-ttu-id="f5044-108">❌NE fournissez pas de champs d’instance publics ou protégés.</span><span class="sxs-lookup"><span data-stu-id="f5044-108">❌ DO NOT provide instance fields that are public or protected.</span></span>

 <span data-ttu-id="f5044-109">Vous devez fournir des propriétés pour accéder aux champs au lieu de les rendre publics ou protégés.</span><span class="sxs-lookup"><span data-stu-id="f5044-109">You should provide properties for accessing fields instead of making them public or protected.</span></span>

 <span data-ttu-id="f5044-110">✔️ Utilisez des champs constants pour les constantes qui ne changeront jamais.</span><span class="sxs-lookup"><span data-stu-id="f5044-110">✔️ DO use constant fields for constants that will never change.</span></span>

 <span data-ttu-id="f5044-111">Le compilateur grave les valeurs des champs const directement dans le code appelant.</span><span class="sxs-lookup"><span data-stu-id="f5044-111">The compiler burns the values of const fields directly into calling code.</span></span> <span data-ttu-id="f5044-112">Par conséquent, les valeurs const ne peuvent jamais être modifiées sans risque d’interruption de la compatibilité.</span><span class="sxs-lookup"><span data-stu-id="f5044-112">Therefore, const values can never be changed without the risk of breaking compatibility.</span></span>

 <span data-ttu-id="f5044-113">✔️ Utilisez des champs statiques publics `readonly` pour les instances d’objet prédéfinies.</span><span class="sxs-lookup"><span data-stu-id="f5044-113">✔️ DO use public static `readonly` fields for predefined object instances.</span></span>

 <span data-ttu-id="f5044-114">S’il existe des instances prédéfinies du type, déclarez-les en tant que champs statiques publics en lecture seule du type lui-même.</span><span class="sxs-lookup"><span data-stu-id="f5044-114">If there are predefined instances of the type, declare them as public read-only static fields of the type itself.</span></span>

 <span data-ttu-id="f5044-115">❌N’assignez pas d’instances de types mutables à des `readonly` champs.</span><span class="sxs-lookup"><span data-stu-id="f5044-115">❌ DO NOT assign instances of mutable types to `readonly` fields.</span></span>

 <span data-ttu-id="f5044-116">Un type mutable est un type dont les instances peuvent être modifiées une fois qu’elles ont été instanciées.</span><span class="sxs-lookup"><span data-stu-id="f5044-116">A mutable type is a type with instances that can be modified after they are instantiated.</span></span> <span data-ttu-id="f5044-117">Par exemple, les tableaux, la plupart des collections et des flux sont des types mutables, mais <xref:System.Int32?displayProperty=nameWithType> , <xref:System.Uri?displayProperty=nameWithType> et <xref:System.String?displayProperty=nameWithType> sont tous immuables.</span><span class="sxs-lookup"><span data-stu-id="f5044-117">For example, arrays, most collections, and streams are mutable types, but <xref:System.Int32?displayProperty=nameWithType>, <xref:System.Uri?displayProperty=nameWithType>, and <xref:System.String?displayProperty=nameWithType> are all immutable.</span></span> <span data-ttu-id="f5044-118">Le modificateur en lecture seule sur un champ de type référence empêche le remplacement de l’instance stockée dans le champ, mais n’empêche pas la modification des données d’instance du champ en appelant des membres qui modifient l’instance.</span><span class="sxs-lookup"><span data-stu-id="f5044-118">The read-only modifier on a reference type field prevents the instance stored in the field from being replaced, but it does not prevent the field’s instance data from being modified by calling members changing the instance.</span></span>

 <span data-ttu-id="f5044-119">*Parties © 2005, 2009 Microsoft Corporation. Tous droits réservés.*</span><span class="sxs-lookup"><span data-stu-id="f5044-119">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>

 <span data-ttu-id="f5044-120">*Réimprimé avec l’autorisation de Pearson Education, Inc. et extrait de [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) par Krzysztof Cwalina et Brad Abrams, publié le 22 octobre 2008 par Addison-Wesley Professional dans le cadre de la série sur le développement Microsoft Windows.*</span><span class="sxs-lookup"><span data-stu-id="f5044-120">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>

## <a name="see-also"></a><span data-ttu-id="f5044-121">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f5044-121">See also</span></span>

- [<span data-ttu-id="f5044-122">Recommandations en matière de conception de membres</span><span class="sxs-lookup"><span data-stu-id="f5044-122">Member Design Guidelines</span></span>](member.md)
- [<span data-ttu-id="f5044-123">Directives de conception d’infrastructure</span><span class="sxs-lookup"><span data-stu-id="f5044-123">Framework Design Guidelines</span></span>](index.md)
