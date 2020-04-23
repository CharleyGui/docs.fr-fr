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
ms.openlocfilehash: 2fc74990b15caaa9b58e6eea5b0212ea22505674
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "82071828"
---
# <a name="xamlname-grammar"></a><span data-ttu-id="06c5e-102">XamlName, grammaire</span><span class="sxs-lookup"><span data-stu-id="06c5e-102">XamlName Grammar</span></span>

<span data-ttu-id="06c5e-103">XamlName Grammar est une grammaire spécifique qui est définie dans la spécification de la langue XAML [MS-XAML], qui est reproduit ici pour plus de commodité.</span><span class="sxs-lookup"><span data-stu-id="06c5e-103">XamlName Grammar is a specific grammar that is defined in the XAML language specification [MS-XAML], which is reproduced here for convenience.</span></span>

## <a name="from-the-xaml-specification"></a><span data-ttu-id="06c5e-104">De la spécification XAML</span><span class="sxs-lookup"><span data-stu-id="06c5e-104">From the XAML Specification</span></span>

<span data-ttu-id="06c5e-105">La spécification [MS-XAML] définit la grammaire XamlName pour identifier l’ensemble des identificateurs symboliques juridiques utilisés pour les types et les propriétés.</span><span class="sxs-lookup"><span data-stu-id="06c5e-105">The [MS-XAML] specification defines the grammar XamlName to identify the set of legal symbolic identifiers used for types and properties.</span></span>

<span data-ttu-id="06c5e-106">Les valeurs de chaîne de type XamlName doivent se conformer à la grammaire suivante :</span><span class="sxs-lookup"><span data-stu-id="06c5e-106">String values that are of type XamlName must conform to the following grammar:</span></span>

```xaml
XamlName ::= NameStartChar ( NameChar )*
NameStartChar ::= LetterCharacter | '_'
NameChar ::= NameStartChar | DecimalDigit | CombiningCharacter
LetterCharacter ::= UnicodeLu | UnicodeLl | UnicodeLo | UnicodeLt | UnicodeNl
DecimalDigit ::= UnicodeNd
CombiningCharacter ::= UnicodeMn | UnicodeMc
```

<span data-ttu-id="06c5e-107">Ce qui suppose les valeurs de catégorie générale suivantes telles que définies dans la base de données sur les caractères Unicode</span><span class="sxs-lookup"><span data-stu-id="06c5e-107">Which assumes the following general category values as defined in the Unicode Character Database</span></span>

| <span data-ttu-id="06c5e-108">Catégorie Unicode</span><span class="sxs-lookup"><span data-stu-id="06c5e-108">Unicode category</span></span>   | <span data-ttu-id="06c5e-109">Description</span><span class="sxs-lookup"><span data-stu-id="06c5e-109">Description</span></span>                   |
|--------------------|-------------------------------|
| <span data-ttu-id="06c5e-110">Lu</span><span class="sxs-lookup"><span data-stu-id="06c5e-110">Lu</span></span>                 | <span data-ttu-id="06c5e-111">Letter, Uppercase</span><span class="sxs-lookup"><span data-stu-id="06c5e-111">Letter, Uppercase</span></span>             |
| <span data-ttu-id="06c5e-112">Ll</span><span class="sxs-lookup"><span data-stu-id="06c5e-112">Ll</span></span>                 | <span data-ttu-id="06c5e-113">Letter, Lowercase</span><span class="sxs-lookup"><span data-stu-id="06c5e-113">Letter, Lowercase</span></span>             |
| <span data-ttu-id="06c5e-114">Lt</span><span class="sxs-lookup"><span data-stu-id="06c5e-114">Lt</span></span>                 | <span data-ttu-id="06c5e-115">Letter, Titlecase</span><span class="sxs-lookup"><span data-stu-id="06c5e-115">Letter, Titlecase</span></span>             |
| <span data-ttu-id="06c5e-116">Lm</span><span class="sxs-lookup"><span data-stu-id="06c5e-116">Lm</span></span>                 | <span data-ttu-id="06c5e-117">Letter, Modifier</span><span class="sxs-lookup"><span data-stu-id="06c5e-117">Letter, Modifier</span></span>              |
| <span data-ttu-id="06c5e-118">Lo</span><span class="sxs-lookup"><span data-stu-id="06c5e-118">Lo</span></span>                 | <span data-ttu-id="06c5e-119">Letter, Other</span><span class="sxs-lookup"><span data-stu-id="06c5e-119">Letter, Other</span></span>                 |
| <span data-ttu-id="06c5e-120">Mn</span><span class="sxs-lookup"><span data-stu-id="06c5e-120">Mn</span></span>                 | <span data-ttu-id="06c5e-121">Marque, Non-Spacing</span><span class="sxs-lookup"><span data-stu-id="06c5e-121">Mark, Non-Spacing</span></span>             |
| <span data-ttu-id="06c5e-122">Mc</span><span class="sxs-lookup"><span data-stu-id="06c5e-122">Mc</span></span>                 | <span data-ttu-id="06c5e-123">Mark, Spacing Combining</span><span class="sxs-lookup"><span data-stu-id="06c5e-123">Mark, Spacing Combining</span></span>       |
| <span data-ttu-id="06c5e-124">Nd</span><span class="sxs-lookup"><span data-stu-id="06c5e-124">Nd</span></span>                 | <span data-ttu-id="06c5e-125">Nombre, Décimale</span><span class="sxs-lookup"><span data-stu-id="06c5e-125">Number, Decimal</span></span>               |
| <span data-ttu-id="06c5e-126">Nl</span><span class="sxs-lookup"><span data-stu-id="06c5e-126">Nl</span></span>                 | <span data-ttu-id="06c5e-127">Number, Letter</span><span class="sxs-lookup"><span data-stu-id="06c5e-127">Number, Letter</span></span>                |

<span data-ttu-id="06c5e-128">XAML définit une deuxième grammaire, DottedXamlName, qui est utilisée pour les références qualifiées de propriété et d’événement, et aussi pour les membres ci-joints.</span><span class="sxs-lookup"><span data-stu-id="06c5e-128">XAML defines a second grammar, DottedXamlName, that is used for property and event qualified references, and also for attached members.</span></span> <span data-ttu-id="06c5e-129">Pour plus d’informations, voir <xref:System.Windows.DependencyProperty> et [XAML Aperçu (WPF)](../fundamentals/xaml.md).</span><span class="sxs-lookup"><span data-stu-id="06c5e-129">For more information, see <xref:System.Windows.DependencyProperty> and [XAML Overview (WPF)](../fundamentals/xaml.md).</span></span>

<span data-ttu-id="06c5e-130">Les valeurs de chaîne qui sont de type DottedXamlName doivent se conformer à la grammaire suivante :</span><span class="sxs-lookup"><span data-stu-id="06c5e-130">String values that are of type DottedXamlName must conform to the following grammar:</span></span>

```xaml
DottedXamlName ::= XamlName '.' XamlName
```

## <a name="remarks"></a><span data-ttu-id="06c5e-131">Notes</span><span class="sxs-lookup"><span data-stu-id="06c5e-131">Remarks</span></span>

<span data-ttu-id="06c5e-132">Pour les spécifications complètes, voir [ \[MS-XAML\]](https://docs.microsoft.com/previous-versions/msp-n-p/ff650760(v=pandp.10)).</span><span class="sxs-lookup"><span data-stu-id="06c5e-132">For the complete specification, see [\[MS-XAML\]](https://docs.microsoft.com/previous-versions/msp-n-p/ff650760(v=pandp.10)).</span></span>
