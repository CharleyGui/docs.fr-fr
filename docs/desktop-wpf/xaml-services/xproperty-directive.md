---
title: x:Property, directive
ms.date: 03/30/2017
ms.assetid: 618555a8-c893-455c-810f-ac54cd24ef10
ms.openlocfilehash: d4294b39ff262198f8082863d23eb6f4edbc7054
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90549299"
---
# <a name="xproperty-directive"></a><span data-ttu-id="1fb9d-102">x:Property, directive</span><span class="sxs-lookup"><span data-stu-id="1fb9d-102">x:Property Directive</span></span>

<span data-ttu-id="1fb9d-103">Déclare une propriété XAML dans le balisage.</span><span class="sxs-lookup"><span data-stu-id="1fb9d-103">Declares a XAML property in markup.</span></span>

## <a name="xaml-object-element-usage"></a><span data-ttu-id="1fb9d-104">Utilisation d'éléments objet XAML</span><span class="sxs-lookup"><span data-stu-id="1fb9d-104">XAML Object Element Usage</span></span>

```xaml
<object x:Class="className">
  <x:Members>
    <x:Property Name="propertyName" Type="propertyType"/>
    additionalProperties
  </x:Members>
</object>
```

## <a name="xaml-values"></a><span data-ttu-id="1fb9d-105">Valeurs XAML</span><span class="sxs-lookup"><span data-stu-id="1fb9d-105">XAML Values</span></span>

|||
|-|-|
|`className`|<span data-ttu-id="1fb9d-106">Nom de la classe de stockage ou de la classe partielle pour la production XAML.</span><span class="sxs-lookup"><span data-stu-id="1fb9d-106">Name of the backing class or partial class for the XAML production.</span></span>|
|`propertyName`|<span data-ttu-id="1fb9d-107">Nom de membre de la propriété définie.</span><span class="sxs-lookup"><span data-stu-id="1fb9d-107">Member name of the property being defined.</span></span>|
|`propertyType`|<span data-ttu-id="1fb9d-108">Tapez le nom (ou une autre forme de chaîne, propre à l'infrastructure) qui spécifie le type de cette propriété.</span><span class="sxs-lookup"><span data-stu-id="1fb9d-108">Type name (or other string form, framework-specific) that specifies the type of this property.</span></span>|

## <a name="remarks"></a><span data-ttu-id="1fb9d-109">Notes</span><span class="sxs-lookup"><span data-stu-id="1fb9d-109">Remarks</span></span>

<span data-ttu-id="1fb9d-110">Dans l’implémentation des services XAML .NET,.</span><span class="sxs-lookup"><span data-stu-id="1fb9d-110">In .NET XAML Services implementation, .</span></span> <span data-ttu-id="1fb9d-111">`x:Property` n'a pas de stockage de type direct, mais est pris en charge par la classe <xref:System.Windows.Markup.PropertyDefinition>.</span><span class="sxs-lookup"><span data-stu-id="1fb9d-111">`x:Property` does not have a direct type backing, but is supported by the <xref:System.Windows.Markup.PropertyDefinition> class.</span></span> <span data-ttu-id="1fb9d-112">Dans un flux de nœud XAML, un élément `x:Property` est représenté en tant que membre nommé `Property`, à partir de l'espace de noms XAML du langage XAML.</span><span class="sxs-lookup"><span data-stu-id="1fb9d-112">In a XAML node stream, an `x:Property` element is represented as a member named `Property`, from the XAML language XAML namespace.</span></span> <span data-ttu-id="1fb9d-113">Le membre `Property` contient les attributs déclarés par le balisage.</span><span class="sxs-lookup"><span data-stu-id="1fb9d-113">The member `Property` hold attributes as declared by markup.</span></span>

<span data-ttu-id="1fb9d-114">La signification de `Name` et ne `Type` sont pas assignées au niveau des services XAML .net.</span><span class="sxs-lookup"><span data-stu-id="1fb9d-114">The meaning of `Name` and `Type` are not assigned at .NET XAML Services level.</span></span> <span data-ttu-id="1fb9d-115">Elles est stockée dans le flux de nœud XAML initial sous forme de valeur de chaîne, afin d’être interprétée ultérieurement selon les règles pouvant être imposées par les infrastructures spécifiques.</span><span class="sxs-lookup"><span data-stu-id="1fb9d-115">They are stored in the initial XAML node stream as string values, to be interpreted later under the rules that might be imposed by specific frameworks.</span></span> <span data-ttu-id="1fb9d-116">La signification peut s'aligner sur celle d'un nom et d'un type XAML, ou être valide uniquement dans un système de type de stockage, selon l'implémentation.</span><span class="sxs-lookup"><span data-stu-id="1fb9d-116">The meaning might align to a XAML name and XAML type meaning, or might only be valid in a backing type system, depending on the implementation.</span></span>

<span data-ttu-id="1fb9d-117">Pour pouvoir utiliser `x:Members` afin de spécifier des définitions de membre dans le balisage, les membres doivent être associés à une classe modifiable.</span><span class="sxs-lookup"><span data-stu-id="1fb9d-117">To support a practical usage of `x:Members` as a means to specify member definitions in markup, the members must be associated with a class that can be modified.</span></span> <span data-ttu-id="1fb9d-118">Dans le modèle prévu, `x:Members` existe en tant que membre d'un type qui spécifie un objet `x:Class`.</span><span class="sxs-lookup"><span data-stu-id="1fb9d-118">The intended model is that `x:Members` exists as a member of a type that specifies an `x:Class`.</span></span> <span data-ttu-id="1fb9d-119">Toutefois, le mécanisme d’association de types et de membres ou de génération de définitions de membres dynamiques n’est pas pris en charge au niveau des services XAML .NET.</span><span class="sxs-lookup"><span data-stu-id="1fb9d-119">However, the mechanism for associating types and members or for producing dynamic member definitions is not supported at .NET XAML Services level.</span></span> <span data-ttu-id="1fb9d-120">En revanche, chaque infrastructure dispose de modèles d'application qui prennent en charge les définitions de membre XAML.</span><span class="sxs-lookup"><span data-stu-id="1fb9d-120">This is left to individual frameworks that have application models that support member definitions from XAML.</span></span> <span data-ttu-id="1fb9d-121">Généralement, les actions de génération MSBUILD qui balisent-compilent le XAML et, soit lui intègre du code-behind, soit produisent des assemblys purement XAML, sont nécessaires pour prendre en charge cette fonctionnalité.</span><span class="sxs-lookup"><span data-stu-id="1fb9d-121">Typically, MSBUILD build actions that markup-compile the XAML and either integrate it with code-behind or produce pure from-XAML assemblies are needed to support that feature.</span></span>

## <a name="xproperty-for-windows-workflow-foundation"></a><span data-ttu-id="1fb9d-122">X:Property pour Windows Workflow Foundation</span><span class="sxs-lookup"><span data-stu-id="1fb9d-122">x:Property for Windows Workflow Foundation</span></span>

<span data-ttu-id="1fb9d-123">Pour Windows Workflow Foundation, `x:Property` définit les membres d'une activité personnalisée entièrement composée en XAML ou des membres dynamiques définis en XAML pour un ActivityDesigner avec code-behind.</span><span class="sxs-lookup"><span data-stu-id="1fb9d-123">For Windows Workflow Foundation, `x:Property` defines the members of a custom activity composed entirely in XAML, or XAML –defined dynamic members for an activity designer with code-behind.</span></span> <span data-ttu-id="1fb9d-124">L'objet `x:Class` doit également être spécifié sur l'élément racine de la production XAML.</span><span class="sxs-lookup"><span data-stu-id="1fb9d-124">`x:Class` must also be specified on the root element of the XAML production.</span></span> <span data-ttu-id="1fb9d-125">Ce n’est pas une exigence au niveau des services XAML .NET, mais elle devient une exigence lorsque la production XAML est chargée par les actions de génération MSBUILD qui prennent en charge les activités personnalisées et Windows Workflow Foundation XAML en général.</span><span class="sxs-lookup"><span data-stu-id="1fb9d-125">This is not a requirement at .NET XAML Services level, but becomes a requirement when the XAML production is loaded by the MSBUILD build actions that support custom activities and Windows Workflow Foundation XAML in general.</span></span> <span data-ttu-id="1fb9d-126">Windows Workflow Foundation n’utilise pas le nom de type XAML pur comme valeur prévue pour l' `x:Property` `Type` attribut, et utilise à la place une convention qui n’est pas documentée ici.</span><span class="sxs-lookup"><span data-stu-id="1fb9d-126">Windows Workflow Foundation does not use the pure XAML type name as its intended value for the `x:Property` `Type` attribute, and instead uses a convention that is not documented here.</span></span> <span data-ttu-id="1fb9d-127">Pour plus d’informations, consultez [création de DynamicActivity](/previous-versions/dotnet/netframework-4.0/dd807392(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="1fb9d-127">For more information, see [DynamicActivity Creation](/previous-versions/dotnet/netframework-4.0/dd807392(v=vs.100)).</span></span>
