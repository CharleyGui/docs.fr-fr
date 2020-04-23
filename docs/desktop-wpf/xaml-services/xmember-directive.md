---
title: x:Member, directive
ms.date: 03/30/2017
ms.assetid: 4d8394ef-644c-4331-b6c5-be855d392980
ms.openlocfilehash: e82bb6397404ee466a12ab438585ae1898c34d1a
ms.sourcegitcommit: c2d9718996402993cf31541f11e95531bc68bad0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/27/2020
ms.locfileid: "82071471"
---
# <a name="xmember-directive"></a><span data-ttu-id="74b99-102">x:Member, directive</span><span class="sxs-lookup"><span data-stu-id="74b99-102">x:Member Directive</span></span>
<span data-ttu-id="74b99-103">Déclare un membre XAML dans le balisage.</span><span class="sxs-lookup"><span data-stu-id="74b99-103">Declares a XAML member in markup.</span></span>

## <a name="xaml-object-element-usage"></a><span data-ttu-id="74b99-104">Utilisation d'éléments objet XAML</span><span class="sxs-lookup"><span data-stu-id="74b99-104">XAML Object Element Usage</span></span>

```xaml
<object x:Class="className">
  <x:Members>
    <x:Member Name="propertyName"/>
    additionalMembers
  </x:Members>
</object>
```

## <a name="xaml-values"></a><span data-ttu-id="74b99-105">Valeurs XAML</span><span class="sxs-lookup"><span data-stu-id="74b99-105">XAML Values</span></span>

|||
|-|-|
|`className`|<span data-ttu-id="74b99-106">Nom de la classe de stockage ou de la classe partielle pour la production XAML.</span><span class="sxs-lookup"><span data-stu-id="74b99-106">Name of the backing class or partial class for the XAML production.</span></span>|
|`memberName`|<span data-ttu-id="74b99-107">Nom de membre de la propriété définie.</span><span class="sxs-lookup"><span data-stu-id="74b99-107">Member name of the property being defined.</span></span>|

## <a name="remarks"></a><span data-ttu-id="74b99-108">Notes</span><span class="sxs-lookup"><span data-stu-id="74b99-108">Remarks</span></span>

<span data-ttu-id="74b99-109">Dans .NET XAML Services mise en œuvre, .</span><span class="sxs-lookup"><span data-stu-id="74b99-109">In .NET XAML Services implementation, .</span></span> <span data-ttu-id="74b99-110">`x:Member` n'a pas de stockage de type direct, mais est pris en charge par la classe <xref:System.Windows.Markup.MemberDefinition>.</span><span class="sxs-lookup"><span data-stu-id="74b99-110">`x:Member` does not have a direct type backing, but is supported by the <xref:System.Windows.Markup.MemberDefinition> class.</span></span> <span data-ttu-id="74b99-111">Dans un flux de nœud XAML, un élément `x:Member` est représenté en tant que membre nommé `Member`, à partir de l'espace de noms XAML du langage XAML.</span><span class="sxs-lookup"><span data-stu-id="74b99-111">In a XAML node stream, an `x:Member` element is represented as a member named `Member`, from the XAML language XAML namespace.</span></span> <span data-ttu-id="74b99-112">Le membre `Member` contient les attributs déclarés par le balisage.</span><span class="sxs-lookup"><span data-stu-id="74b99-112">The member `Member` holds attributes as declared by markup.</span></span>

<span data-ttu-id="74b99-113">Le sens `Name` `Type` et ne sont pas attribués au niveau .NET XAML Services.</span><span class="sxs-lookup"><span data-stu-id="74b99-113">The meaning of `Name` and `Type` are not assigned at .NET XAML Services level.</span></span> <span data-ttu-id="74b99-114">Elles est stockée dans le flux de nœud XAML initial sous forme de valeur de chaîne, afin d’être interprétée ultérieurement selon les règles pouvant être imposées par les infrastructures spécifiques.</span><span class="sxs-lookup"><span data-stu-id="74b99-114">They are stored in the initial XAML node stream as string values, to be interpreted later under the rules that might be imposed by specific frameworks.</span></span> <span data-ttu-id="74b99-115">La signification peut s'aligner sur celle d'un nom et d'un type XAML, ou être valide uniquement dans un système de type de stockage, selon l'implémentation.</span><span class="sxs-lookup"><span data-stu-id="74b99-115">The meaning might align to a XAML name and XAML type meaning, or might only be valid in a backing type system, depending on the implementation.</span></span>

<span data-ttu-id="74b99-116">Pour pouvoir utiliser `x:Members` afin de spécifier des définitions de membre dans le balisage, les membres doivent être associés à une classe modifiable.</span><span class="sxs-lookup"><span data-stu-id="74b99-116">To support a practical usage of `x:Members` as a means to specify member definitions in markup, the members must be associated with a class that can be modified.</span></span> <span data-ttu-id="74b99-117">Dans le modèle prévu, `x:Members` existe en tant que membre d'un type qui spécifie un objet `x:Class`.</span><span class="sxs-lookup"><span data-stu-id="74b99-117">The intended model is that `x:Members` exists as a member of a type that specifies an `x:Class`.</span></span> <span data-ttu-id="74b99-118">Cependant, le mécanisme d’association des types et des membres ou pour produire des définitions dynamiques des membres n’est pas pris en charge au niveau .NET XAML Services.</span><span class="sxs-lookup"><span data-stu-id="74b99-118">However, the mechanism for associating types and members or for producing dynamic member definitions is not supported at .NET XAML Services level.</span></span> <span data-ttu-id="74b99-119">En revanche, chaque infrastructure dispose de modèles d'application qui prennent en charge les définitions de membre XAML.</span><span class="sxs-lookup"><span data-stu-id="74b99-119">This is left to individual frameworks that have application models that support member definitions from XAML.</span></span> <span data-ttu-id="74b99-120">Généralement, les actions de génération MSBUILD qui balisent-compilent le XAML et, soit lui intègre du code-behind, soit produisent des assemblys purement XAML, sont nécessaires pour prendre en charge cette fonctionnalité.</span><span class="sxs-lookup"><span data-stu-id="74b99-120">Typically, MSBUILD build actions that markup-compile the XAML and either integrate it with code-behind or produce pure from-XAML assemblies are needed to support that feature.</span></span>

## <a name="xproperty-for-windows-workflow-foundation"></a><span data-ttu-id="74b99-121">X:Property pour Windows Workflow Foundation</span><span class="sxs-lookup"><span data-stu-id="74b99-121">x:Property for Windows Workflow Foundation</span></span>

<span data-ttu-id="74b99-122">Pour Windows Workflow Foundation, `x:Property` définit les membres d'une activité personnalisée entièrement composée en XAML ou des membres dynamiques définis en XAML pour un ActivityDesigner avec code-behind.</span><span class="sxs-lookup"><span data-stu-id="74b99-122">For Windows Workflow Foundation, `x:Property` defines the members of a custom activity composed entirely in XAML, or XAML –defined dynamic members for an activity designer with code-behind.</span></span> <span data-ttu-id="74b99-123">L'objet `x:Class` doit également être spécifié sur l'élément racine de la production XAML.</span><span class="sxs-lookup"><span data-stu-id="74b99-123">`x:Class` must also be specified on the root element of the XAML production.</span></span> <span data-ttu-id="74b99-124">Ce n’est pas une exigence au niveau .NET XAML Services, mais devient une exigence lorsque la production XAML est chargée par le MSBUILD construire des actions qui prennent en charge les activités personnalisées et Windows Workflow Foundation XAML en général.</span><span class="sxs-lookup"><span data-stu-id="74b99-124">This is not a requirement at .NET XAML Services level, but becomes a requirement when the XAML production is loaded by the MSBUILD build actions that support custom activities and Windows Workflow Foundation XAML in general.</span></span> <span data-ttu-id="74b99-125">Windows Workflow Foundation n’utilise pas le nom de type `x:Property` `Type` XAML pur comme valeur prévue pour l’attribut, et utilise plutôt une convention qui n’est pas documentée ici.</span><span class="sxs-lookup"><span data-stu-id="74b99-125">Windows Workflow Foundation does not use the pure XAML type name as its intended value for the `x:Property` `Type` attribute, and instead uses a convention that is not documented here.</span></span> <span data-ttu-id="74b99-126">Pour plus d’informations, voir [DynamicActivity Creation](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/dd807392(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="74b99-126">For more information, see [DynamicActivity Creation](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/dd807392(v=vs.100)).</span></span>
