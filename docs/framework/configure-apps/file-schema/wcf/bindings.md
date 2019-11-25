---
title: <bindings>
ms.date: 01/22/2018
ms.assetid: b62cd369-5409-4030-8490-9759a462dd3a
ms.openlocfilehash: fe8f620668e35183890b8bba1f254a74c962f8d3
ms.sourcegitcommit: fbb8a593a511ce667992502a3ce6d8f65c594edf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/16/2019
ms.locfileid: "74139666"
---
# <a name="bindings"></a><span data-ttu-id="c6abd-101">liaisons de \<</span><span class="sxs-lookup"><span data-stu-id="c6abd-101">\<bindings></span></span>

<span data-ttu-id="c6abd-102">Vous pouvez utiliser l’élément `bindings` pour configurer une collection de liaisons standard et personnalisées pour Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="c6abd-102">You can use the `bindings` element to configure a collection of standard and custom bindings for Windows Communication Foundation (WCF).</span></span> <span data-ttu-id="c6abd-103">Chaque entrée est un élément de `binding` qui peut être identifié par son `name` unique.</span><span class="sxs-lookup"><span data-stu-id="c6abd-103">Each entry is a `binding` element that can be identified by its unique `name`.</span></span> <span data-ttu-id="c6abd-104">Les services utilisent les liaisons en les liant à l’aide de `name`.</span><span class="sxs-lookup"><span data-stu-id="c6abd-104">Services use bindings by linking them using the `name`.</span></span> <span data-ttu-id="c6abd-105">À compter de .NET Framework 4, les liaisons et les comportements n’ont pas besoin d’un nom.</span><span class="sxs-lookup"><span data-stu-id="c6abd-105">Starting with .NET Framework 4, bindings and behaviors are not required to have a name.</span></span> <span data-ttu-id="c6abd-106">Pour plus d’informations sur la configuration par défaut et les liaisons et les comportements sans valeur, consultez [configuration simplifiée](../../../wcf/simplified-configuration.md) et [configuration simplifiée pour les services WCF](../../../wcf/samples/simplified-configuration-for-wcf-services.md).</span><span class="sxs-lookup"><span data-stu-id="c6abd-106">For more information about default configuration and nameless bindings and behaviors, see [Simplified Configuration](../../../wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>

## <a name="system-provided-bindings"></a><span data-ttu-id="c6abd-107">Liaisons fournies par le système</span><span class="sxs-lookup"><span data-stu-id="c6abd-107">System-provided bindings</span></span>

<span data-ttu-id="c6abd-108">Les liaisons fournies par le système masquent la complexité de la pile de la messagerie du WCF.</span><span class="sxs-lookup"><span data-stu-id="c6abd-108">System-provided bindings hide the complexity of the WCF messaging stack.</span></span> <span data-ttu-id="c6abd-109">Les applications qui utilisent des liaisons fournies par le système ne requièrent pas de contrôle total sur la pile.</span><span class="sxs-lookup"><span data-stu-id="c6abd-109">Applications using system-provided bindings do not require full control over the stack.</span></span> <span data-ttu-id="c6abd-110">Les attributs exposés sur chaque liaison fournie par le système sont les plus appropriés pour le scénario d'utilisation des adresses de liaison.</span><span class="sxs-lookup"><span data-stu-id="c6abd-110">The attributes exposed on each system-provided binding are the ones most appropriate for the usage scenario the binding addresses.</span></span>

<span data-ttu-id="c6abd-111">La section de configuration de chaque liaison fournie par le système peut définir plusieurs configurations utilisées en vue de configurer la liaison.</span><span class="sxs-lookup"><span data-stu-id="c6abd-111">The configuration section for each system-provided binding can define several configurations used to configure the binding.</span></span> <span data-ttu-id="c6abd-112">Chaque configuration est identifiée par un nom unique.</span><span class="sxs-lookup"><span data-stu-id="c6abd-112">Each configuration is identified by a unique name.</span></span>

<span data-ttu-id="c6abd-113">Il n’est pas possible d’ajouter des éléments ou des attributs à une liaison fournie par le système.</span><span class="sxs-lookup"><span data-stu-id="c6abd-113">It isn't possible to add elements or attributes to a system-provided binding.</span></span> <span data-ttu-id="c6abd-114">Pour ce faire, vous devez implémenter une liaison personnalisée comme décrit dans la section [liaisons personnalisées](#custom-bindings) .</span><span class="sxs-lookup"><span data-stu-id="c6abd-114">To do so, you should implement a custom binding as described in the [Custom bindings](#custom-bindings) section.</span></span> <span data-ttu-id="c6abd-115">Il est possible de définir une liaison personnalisée qui imite parfaitement une liaison fournie par le système et ajoute quelques paramètres sur lesquels l’application utilisateur souhaite avoir le contrôle.</span><span class="sxs-lookup"><span data-stu-id="c6abd-115">It's possible to define a custom binding that mimics a system-provided binding perfectly and adds a few settings the user application wants to have control over.</span></span>  

<span data-ttu-id="c6abd-116">Pour obtenir la liste des liaisons fournies par le système, consultez [liaisons fournies par le système](../../../wcf/system-provided-bindings.md).</span><span class="sxs-lookup"><span data-stu-id="c6abd-116">For a list of system-provided bindings, see [System-Provided Bindings](../../../wcf/system-provided-bindings.md).</span></span>

## <a name="custom-bindings"></a><span data-ttu-id="c6abd-117">Liaisons personnalisées</span><span class="sxs-lookup"><span data-stu-id="c6abd-117">Custom bindings</span></span>

<span data-ttu-id="c6abd-118">Les liaisons personnalisées permettent d'exercer un contrôle total sur la pile de messagerie WCF.</span><span class="sxs-lookup"><span data-stu-id="c6abd-118">Custom bindings provide full control over the WCF messaging stack.</span></span> <span data-ttu-id="c6abd-119">Une liaison individuelle définit la pile de messages en spécifiant les éléments de configuration des éléments de la pile suivant leur l'ordre d'apparition dans cette pile.</span><span class="sxs-lookup"><span data-stu-id="c6abd-119">An individual binding defines the message stack by specifying the configuration elements for the stack elements in the order they appear on the stack.</span></span> <span data-ttu-id="c6abd-120">Chaque élément définit et configure un élément de la pile.</span><span class="sxs-lookup"><span data-stu-id="c6abd-120">Each element defines and configures one element of the stack.</span></span> <span data-ttu-id="c6abd-121">Il doit y avoir un seul élément de `transport` dans chaque liaison personnalisée.</span><span class="sxs-lookup"><span data-stu-id="c6abd-121">There must be one and only one `transport` element in each custom binding.</span></span> <span data-ttu-id="c6abd-122">Sans cet élément, la pile de messagerie est incomplète.</span><span class="sxs-lookup"><span data-stu-id="c6abd-122">Without this element, the messaging stack is incomplete.</span></span>

<span data-ttu-id="c6abd-123">L'ordre dans lequel les éléments apparaissent dans la pile est important car il s'agit de l'ordre dans lequel les opérations sont appliquées au message.</span><span class="sxs-lookup"><span data-stu-id="c6abd-123">The order in which elements appear in the stack matters, because it is the order in which operations are applied to the message.</span></span> <span data-ttu-id="c6abd-124">Voici l'ordre requis des éléments de la pile :</span><span class="sxs-lookup"><span data-stu-id="c6abd-124">The required order of stack elements is the following:</span></span>  

1. <span data-ttu-id="c6abd-125">Transactions (facultatif)</span><span class="sxs-lookup"><span data-stu-id="c6abd-125">Transactions (optional)</span></span>  

2. <span data-ttu-id="c6abd-126">Messagerie fiable (facultatif)</span><span class="sxs-lookup"><span data-stu-id="c6abd-126">Reliable messaging (optional)</span></span>  

3. <span data-ttu-id="c6abd-127">Sécurité (facultatif)</span><span class="sxs-lookup"><span data-stu-id="c6abd-127">Security (optional)</span></span>  

4. <span data-ttu-id="c6abd-128">Encodeur</span><span class="sxs-lookup"><span data-stu-id="c6abd-128">Encoder</span></span>  

5. <span data-ttu-id="c6abd-129">Transport</span><span class="sxs-lookup"><span data-stu-id="c6abd-129">Transport</span></span>  

 <span data-ttu-id="c6abd-130">Les liaisons personnalisées sont identifiées par leur attribut `name`.</span><span class="sxs-lookup"><span data-stu-id="c6abd-130">Custom bindings are identified by their `name` attribute.</span></span> <span data-ttu-id="c6abd-131">Pour plus d’informations sur les liaisons personnalisées, consultez [liaisons personnalisées](../../../wcf/extending/custom-bindings.md).</span><span class="sxs-lookup"><span data-stu-id="c6abd-131">For more information on custom bindings, see [Custom Bindings](../../../wcf/extending/custom-bindings.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="c6abd-132">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="c6abd-132">See also</span></span>

- <xref:System.ServiceModel.Configuration.BindingsSection?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.Binding?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.BindingElement?displayProperty=nameWithType>
- [<span data-ttu-id="c6abd-133">Liaisons</span><span class="sxs-lookup"><span data-stu-id="c6abd-133">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="c6abd-134">Liaisons personnalisées</span><span class="sxs-lookup"><span data-stu-id="c6abd-134">Custom Bindings</span></span>](../../../wcf/extending/custom-bindings.md)
- [<span data-ttu-id="c6abd-135">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="c6abd-135">\<customBinding></span></span>](custombinding.md)
