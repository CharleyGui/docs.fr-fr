---
title: XamlName, grammaire
ms.date: 03/30/2017
helpviewer_keywords:
- DottedXamlName grammar [XAML Services]
- grammar [XAML Services], DottedXamlName
- grammar [XAML Services], XamlName
- names in XAML [XAML Services]
- XamlName grammar [XAML Services]
ms.assetid: 11e4cada-41d2-494d-9531-0d3df4dfcbe3
ms.openlocfilehash: ceb027938b6d4313babbe02949e0b6dd5ee85589
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90556692"
---
# <a name="xamlname-grammar"></a><span data-ttu-id="a0258-102">XamlName, grammaire</span><span class="sxs-lookup"><span data-stu-id="a0258-102">XamlName Grammar</span></span>

<span data-ttu-id="a0258-103">La grammaire XamlName est une grammaire spécifique qui est définie dans la spécification du langage XAML [MS-XAML], qui est reproduite ici pour des raisons pratiques.</span><span class="sxs-lookup"><span data-stu-id="a0258-103">XamlName Grammar is a specific grammar that is defined in the XAML language specification [MS-XAML], which is reproduced here for convenience.</span></span>

## <a name="from-the-xaml-specification"></a><span data-ttu-id="a0258-104">À partir de la spécification XAML</span><span class="sxs-lookup"><span data-stu-id="a0258-104">From the XAML Specification</span></span>

<span data-ttu-id="a0258-105">La spécification [MS-XAML] définit la grammaire XamlName pour identifier le jeu d’identificateurs symboliques légaux utilisé pour les types et les propriétés.</span><span class="sxs-lookup"><span data-stu-id="a0258-105">The [MS-XAML] specification defines the grammar XamlName to identify the set of legal symbolic identifiers used for types and properties.</span></span>

<span data-ttu-id="a0258-106">Les valeurs de chaîne qui sont de type XamlName doivent respecter la grammaire suivante :</span><span class="sxs-lookup"><span data-stu-id="a0258-106">String values that are of type XamlName must conform to the following grammar:</span></span>

```xaml
XamlName ::= NameStartChar ( NameChar )*
NameStartChar ::= LetterCharacter | '_'
NameChar ::= NameStartChar | DecimalDigit | CombiningCharacter
LetterCharacter ::= UnicodeLu | UnicodeLl | UnicodeLo | UnicodeLt | UnicodeNl
DecimalDigit ::= UnicodeNd
CombiningCharacter ::= UnicodeMn | UnicodeMc
```

<span data-ttu-id="a0258-107">Qui utilise les valeurs de catégorie générale suivantes, telles que définies dans la base de données de caractères Unicode</span><span class="sxs-lookup"><span data-stu-id="a0258-107">Which assumes the following general category values as defined in the Unicode Character Database</span></span>

| <span data-ttu-id="a0258-108">Catégorie Unicode</span><span class="sxs-lookup"><span data-stu-id="a0258-108">Unicode category</span></span>   | <span data-ttu-id="a0258-109">Description</span><span class="sxs-lookup"><span data-stu-id="a0258-109">Description</span></span>                   |
|--------------------|-------------------------------|
| <span data-ttu-id="a0258-110">Lu</span><span class="sxs-lookup"><span data-stu-id="a0258-110">Lu</span></span>                 | <span data-ttu-id="a0258-111">Letter, Uppercase</span><span class="sxs-lookup"><span data-stu-id="a0258-111">Letter, Uppercase</span></span>             |
| <span data-ttu-id="a0258-112">Ll</span><span class="sxs-lookup"><span data-stu-id="a0258-112">Ll</span></span>                 | <span data-ttu-id="a0258-113">Letter, Lowercase</span><span class="sxs-lookup"><span data-stu-id="a0258-113">Letter, Lowercase</span></span>             |
| <span data-ttu-id="a0258-114">Lt</span><span class="sxs-lookup"><span data-stu-id="a0258-114">Lt</span></span>                 | <span data-ttu-id="a0258-115">Letter, Titlecase</span><span class="sxs-lookup"><span data-stu-id="a0258-115">Letter, Titlecase</span></span>             |
| <span data-ttu-id="a0258-116">Lm</span><span class="sxs-lookup"><span data-stu-id="a0258-116">Lm</span></span>                 | <span data-ttu-id="a0258-117">Letter, Modifier</span><span class="sxs-lookup"><span data-stu-id="a0258-117">Letter, Modifier</span></span>              |
| <span data-ttu-id="a0258-118">Lo</span><span class="sxs-lookup"><span data-stu-id="a0258-118">Lo</span></span>                 | <span data-ttu-id="a0258-119">Letter, Other</span><span class="sxs-lookup"><span data-stu-id="a0258-119">Letter, Other</span></span>                 |
| <span data-ttu-id="a0258-120">Mn</span><span class="sxs-lookup"><span data-stu-id="a0258-120">Mn</span></span>                 | <span data-ttu-id="a0258-121">Marquer, sans espace</span><span class="sxs-lookup"><span data-stu-id="a0258-121">Mark, Non-Spacing</span></span>             |
| <span data-ttu-id="a0258-122">Mc</span><span class="sxs-lookup"><span data-stu-id="a0258-122">Mc</span></span>                 | <span data-ttu-id="a0258-123">Mark, Spacing Combining</span><span class="sxs-lookup"><span data-stu-id="a0258-123">Mark, Spacing Combining</span></span>       |
| <span data-ttu-id="a0258-124">Nd</span><span class="sxs-lookup"><span data-stu-id="a0258-124">Nd</span></span>                 | <span data-ttu-id="a0258-125">Nombre, décimal</span><span class="sxs-lookup"><span data-stu-id="a0258-125">Number, Decimal</span></span>               |
| <span data-ttu-id="a0258-126">Nl</span><span class="sxs-lookup"><span data-stu-id="a0258-126">Nl</span></span>                 | <span data-ttu-id="a0258-127">Number, Letter</span><span class="sxs-lookup"><span data-stu-id="a0258-127">Number, Letter</span></span>                |

<span data-ttu-id="a0258-128">XAML définit une deuxième grammaire, DottedXamlName, qui est utilisée pour les références qualifiées de propriété et d’événement, ainsi que pour les membres attachés.</span><span class="sxs-lookup"><span data-stu-id="a0258-128">XAML defines a second grammar, DottedXamlName, that is used for property and event qualified references, and also for attached members.</span></span> <span data-ttu-id="a0258-129">Pour plus d’informations, consultez <xref:System.Windows.DependencyProperty> et [vue d’ensemble du langage XAML (WPF)](../fundamentals/xaml.md).</span><span class="sxs-lookup"><span data-stu-id="a0258-129">For more information, see <xref:System.Windows.DependencyProperty> and [XAML Overview (WPF)](../fundamentals/xaml.md).</span></span>

<span data-ttu-id="a0258-130">Les valeurs de chaîne qui sont de type DottedXamlName doivent être conformes à la grammaire suivante :</span><span class="sxs-lookup"><span data-stu-id="a0258-130">String values that are of type DottedXamlName must conform to the following grammar:</span></span>

```xaml
DottedXamlName ::= XamlName '.' XamlName
```

## <a name="remarks"></a><span data-ttu-id="a0258-131">Notes</span><span class="sxs-lookup"><span data-stu-id="a0258-131">Remarks</span></span>

<span data-ttu-id="a0258-132">Pour obtenir la spécification complète, consultez [ \[ MS- \] XAML](/previous-versions/msp-n-p/ff650760(v=pandp.10)).</span><span class="sxs-lookup"><span data-stu-id="a0258-132">For the complete specification, see [\[MS-XAML\]](/previous-versions/msp-n-p/ff650760(v=pandp.10)).</span></span>
