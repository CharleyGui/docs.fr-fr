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
ms.openlocfilehash: a39d25f03583ab9020878b7a659bc99489231ff9
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/03/2019
ms.locfileid: "73458889"
---
# <a name="xamlname-grammar"></a><span data-ttu-id="59637-102">XamlName, grammaire</span><span class="sxs-lookup"><span data-stu-id="59637-102">XamlName Grammar</span></span>
<span data-ttu-id="59637-103">La grammaire XamlName est une grammaire spécifique qui est définie dans la spécification du langage XAML [MS-XAML], qui est reproduite ici pour des raisons pratiques.</span><span class="sxs-lookup"><span data-stu-id="59637-103">XamlName Grammar is a specific grammar that is defined in the XAML language specification [MS-XAML], which is reproduced here for convenience.</span></span>  
  
## <a name="from-the-xaml-specification"></a><span data-ttu-id="59637-104">À partir de la spécification XAML</span><span class="sxs-lookup"><span data-stu-id="59637-104">From the XAML Specification</span></span>  
 <span data-ttu-id="59637-105">La spécification [MS-XAML] définit la grammaire XamlName pour identifier le jeu d’identificateurs symboliques légaux utilisé pour les types et les propriétés.</span><span class="sxs-lookup"><span data-stu-id="59637-105">The [MS-XAML] specification defines the grammar XamlName to identify the set of legal symbolic identifiers used for types and properties.</span></span>  
  
 <span data-ttu-id="59637-106">Les valeurs de chaîne qui sont de type XamlName doivent respecter la grammaire suivante :</span><span class="sxs-lookup"><span data-stu-id="59637-106">String values that are of type XamlName must conform to the following grammar:</span></span>  
  
```xaml  
XamlName ::= NameStartChar ( NameChar )*   
NameStartChar ::= LetterCharacter | '_'   
NameChar ::= NameStartChar | DecimalDigit | CombiningCharacter   
LetterCharacter ::= UnicodeLu | UnicodeLl | UnicodeLo | UnicodeLt | UnicodeNl   
DecimalDigit ::= UnicodeNd   
CombiningCharacter ::= UnicodeMn | UnicodeMc  
```  
  
 <span data-ttu-id="59637-107">Qui utilise les valeurs de catégorie générale suivantes, telles que définies dans la base de données de caractères Unicode</span><span class="sxs-lookup"><span data-stu-id="59637-107">Which assumes the following general category values as defined in the Unicode Character Database</span></span>  

| <span data-ttu-id="59637-108">Catégorie Unicode</span><span class="sxs-lookup"><span data-stu-id="59637-108">Unicode category</span></span>   | <span data-ttu-id="59637-109">Description</span><span class="sxs-lookup"><span data-stu-id="59637-109">Description</span></span>                   |
|--------------------|-------------------------------|
| <span data-ttu-id="59637-110">Lu</span><span class="sxs-lookup"><span data-stu-id="59637-110">Lu</span></span>                 | <span data-ttu-id="59637-111">Letter, Uppercase</span><span class="sxs-lookup"><span data-stu-id="59637-111">Letter, Uppercase</span></span>             |
| <span data-ttu-id="59637-112">Ll</span><span class="sxs-lookup"><span data-stu-id="59637-112">Ll</span></span>                 | <span data-ttu-id="59637-113">Letter, Lowercase</span><span class="sxs-lookup"><span data-stu-id="59637-113">Letter, Lowercase</span></span>             |
| <span data-ttu-id="59637-114">Lt</span><span class="sxs-lookup"><span data-stu-id="59637-114">Lt</span></span>                 | <span data-ttu-id="59637-115">Letter, Titlecase</span><span class="sxs-lookup"><span data-stu-id="59637-115">Letter, Titlecase</span></span>             |
| <span data-ttu-id="59637-116">Lm</span><span class="sxs-lookup"><span data-stu-id="59637-116">Lm</span></span>                 | <span data-ttu-id="59637-117">Letter, Modifier</span><span class="sxs-lookup"><span data-stu-id="59637-117">Letter, Modifier</span></span>              |
| <span data-ttu-id="59637-118">Lo</span><span class="sxs-lookup"><span data-stu-id="59637-118">Lo</span></span>                 | <span data-ttu-id="59637-119">Letter, Other</span><span class="sxs-lookup"><span data-stu-id="59637-119">Letter, Other</span></span>                 |
| <span data-ttu-id="59637-120">Mn</span><span class="sxs-lookup"><span data-stu-id="59637-120">Mn</span></span>                 | <span data-ttu-id="59637-121">Marquer, sans espace</span><span class="sxs-lookup"><span data-stu-id="59637-121">Mark, Non-Spacing</span></span>             |
| <span data-ttu-id="59637-122">Mc</span><span class="sxs-lookup"><span data-stu-id="59637-122">Mc</span></span>                 | <span data-ttu-id="59637-123">Mark, Spacing Combining</span><span class="sxs-lookup"><span data-stu-id="59637-123">Mark, Spacing Combining</span></span>       |
| <span data-ttu-id="59637-124">Nd</span><span class="sxs-lookup"><span data-stu-id="59637-124">Nd</span></span>                 | <span data-ttu-id="59637-125">Nombre, décimal</span><span class="sxs-lookup"><span data-stu-id="59637-125">Number, Decimal</span></span>               |
| <span data-ttu-id="59637-126">Nl</span><span class="sxs-lookup"><span data-stu-id="59637-126">Nl</span></span>                 | <span data-ttu-id="59637-127">Number, Letter</span><span class="sxs-lookup"><span data-stu-id="59637-127">Number, Letter</span></span>                |
 
 <span data-ttu-id="59637-128">XAML définit une deuxième grammaire, DottedXamlName, qui est utilisée pour les références qualifiées de propriété et d’événement, ainsi que pour les membres attachés.</span><span class="sxs-lookup"><span data-stu-id="59637-128">XAML defines a second grammar, DottedXamlName, that is used for property and event qualified references, and also for attached members.</span></span> <span data-ttu-id="59637-129">Pour plus d’informations, consultez [vue d’ensemble de <xref:System.Windows.DependencyProperty> et XAML (WPF)](../../desktop-wpf/fundamentals/xaml.md).</span><span class="sxs-lookup"><span data-stu-id="59637-129">For more information, see <xref:System.Windows.DependencyProperty> and [XAML Overview (WPF)](../../desktop-wpf/fundamentals/xaml.md).</span></span>  
  
 <span data-ttu-id="59637-130">Les valeurs de chaîne qui sont de type DottedXamlName doivent être conformes à la grammaire suivante :</span><span class="sxs-lookup"><span data-stu-id="59637-130">String values that are of type DottedXamlName must conform to the following grammar:</span></span>  
  
```xaml  
DottedXamlName ::= XamlName '.' XamlName  
```  
  
## <a name="remarks"></a><span data-ttu-id="59637-131">Notes</span><span class="sxs-lookup"><span data-stu-id="59637-131">Remarks</span></span>  
 <span data-ttu-id="59637-132">Pour obtenir la spécification complète, consultez [\[MS-XAML\]](https://go.microsoft.com/fwlink/?LinkId=114525).</span><span class="sxs-lookup"><span data-stu-id="59637-132">For the complete specification, see [\[MS-XAML\]](https://go.microsoft.com/fwlink/?LinkId=114525).</span></span>
