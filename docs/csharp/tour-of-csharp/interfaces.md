---
title: Interfaces C# - Visite guidée du langage C#
description: Les interfaces définissent des contrats implémentés par les types en C#
ms.date: 02/27/2020
ms.assetid: a9bf82f4-efd1-4216-bd34-4ef0fa48c968
ms.openlocfilehash: 62d94462fa481379cf70d63a598deb7f36be204f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "78159128"
---
# <a name="interfaces"></a><span data-ttu-id="8b116-103">Interfaces</span><span class="sxs-lookup"><span data-stu-id="8b116-103">Interfaces</span></span>

<span data-ttu-id="8b116-104">Une ***interface*** définit un contrat qui peut être implémenté par des classes et structures.</span><span class="sxs-lookup"><span data-stu-id="8b116-104">An ***interface*** defines a contract that can be implemented by classes and structs.</span></span> <span data-ttu-id="8b116-105">Une interface peut contenir des méthodes, des propriétés, des événements et des indexeurs.</span><span class="sxs-lookup"><span data-stu-id="8b116-105">An interface can contain methods, properties, events, and indexers.</span></span> <span data-ttu-id="8b116-106">Une interface ne fournit pas les implémentations des membres qu’elle définit, elle spécifie simplement les membres qui doivent être fournis par des classes ou des structs qui implémentent l’interface.</span><span class="sxs-lookup"><span data-stu-id="8b116-106">An interface doesn't provide implementations of the members it defines—it merely specifies the members that must be supplied by classes or structs that implement the interface.</span></span>

<span data-ttu-id="8b116-107">Les interfaces peuvent utiliser ***l’héritage multiple***.</span><span class="sxs-lookup"><span data-stu-id="8b116-107">Interfaces may employ ***multiple inheritance***.</span></span> <span data-ttu-id="8b116-108">Dans l’exemple suivant, l’interface `IComboBox` hérite à la fois de `ITextBox` et `IListBox`.</span><span class="sxs-lookup"><span data-stu-id="8b116-108">In the following example, the interface `IComboBox` inherits from both `ITextBox` and `IListBox`.</span></span>

[!code-csharp[InterfacesOne](../../../samples/snippets/csharp/tour/interfaces/Program.cs#L5-L17)]

<span data-ttu-id="8b116-109">Les classes et les structs peuvent implémenter plusieurs interfaces.</span><span class="sxs-lookup"><span data-stu-id="8b116-109">Classes and structs can implement multiple interfaces.</span></span> <span data-ttu-id="8b116-110">Dans l’exemple suivant, la classe `EditBox` implémente à la fois `IControl` et `IDataBound`.</span><span class="sxs-lookup"><span data-stu-id="8b116-110">In the following example, the class `EditBox` implements both `IControl` and `IDataBound`.</span></span>

[!code-csharp[InterfacesTwo](../../../samples/snippets/csharp/tour/interfaces/Program.cs#L19-L27)]

<span data-ttu-id="8b116-111">Lorsqu’une classe ou un struct implémente une interface spécifique, les instances de cette classe ou struct peuvent être converties implicitement en ce type d’interface.</span><span class="sxs-lookup"><span data-stu-id="8b116-111">When a class or struct implements a particular interface, instances of that class or struct can be implicitly converted to that interface type.</span></span> <span data-ttu-id="8b116-112">Par exemple</span><span class="sxs-lookup"><span data-stu-id="8b116-112">For example</span></span>

[!code-csharp[InterfacesThree](../../../samples/snippets/csharp/tour/interfaces/Program.cs#L33-L35)]

<span data-ttu-id="8b116-113">Dans les cas où une instance n’est pas statiquement connue pour implémenter une interface particulière, des moulages de type dynamique peuvent être utilisés.</span><span class="sxs-lookup"><span data-stu-id="8b116-113">In cases where an instance isn't statically known to implement a particular interface, dynamic type casts can be used.</span></span> <span data-ttu-id="8b116-114">Par exemple, les instructions suivantes utilisent des casts de type dynamiques pour obtenir les implémentations des interfaces `IControl` et `IDataBound` d’un objet.</span><span class="sxs-lookup"><span data-stu-id="8b116-114">For example, the following statements use dynamic type casts to obtain an object’s `IControl` and `IDataBound` interface implementations.</span></span> <span data-ttu-id="8b116-115">Étant donné que le type réel au moment de l’exécution de l’objet est `EditBox`, les casts réussissent.</span><span class="sxs-lookup"><span data-stu-id="8b116-115">Because the run-time actual type of the object is `EditBox`, the casts succeed.</span></span>

[!code-csharp[InterfacesFour](../../../samples/snippets/csharp/tour/interfaces/Program.cs#L40-L42)]

<span data-ttu-id="8b116-116">Dans la classe `EditBox` précédente, la méthode `Paint` de l’interface `IControl` et la méthode `Bind` de l’interface `IDataBound` sont implémentées à l’aide des membres publics.</span><span class="sxs-lookup"><span data-stu-id="8b116-116">In the previous `EditBox` class, the `Paint` method from the `IControl` interface and the `Bind` method from the `IDataBound` interface are implemented using public members.</span></span> <span data-ttu-id="8b116-117">C# prend également en charge les ***implémentations de membres d’interface*** explicites, permettant ainsi à la classe ou structure d’éviter d’avoir à créer des membres publics.</span><span class="sxs-lookup"><span data-stu-id="8b116-117">C# also supports explicit ***interface member implementations***, enabling the class or struct to avoid making the members public.</span></span> <span data-ttu-id="8b116-118">Une implémentation de membre d’interface explicite est écrite à l’aide du nom de membre d’interface qualifié complet.</span><span class="sxs-lookup"><span data-stu-id="8b116-118">An explicit interface member implementation is written using the fully qualified interface member name.</span></span> <span data-ttu-id="8b116-119">Par exemple, la classe `EditBox` peut implémenter les méthodes `IControl.Paint` et `IDataBound.Bind` à l’aide des implémentations de membres d’interface explicites, comme suit.</span><span class="sxs-lookup"><span data-stu-id="8b116-119">For example, the `EditBox` class could implement the `IControl.Paint` and `IDataBound.Bind` methods using explicit interface member implementations as follows.</span></span>

[!code-csharp[InterfacesFive](../../../samples/snippets/csharp/tour/interfaces/Program.cs#L60-L64)]

<span data-ttu-id="8b116-120">Les membres d’interface explicites sont accessibles uniquement via le type interface.</span><span class="sxs-lookup"><span data-stu-id="8b116-120">Explicit interface members can only be accessed via the interface type.</span></span> <span data-ttu-id="8b116-121">Par exemple, l’implémentation de `IControl.Paint` fournie par la classe EditBox précédente ne peut être appelée en convertissant d’abord l’ `EditBox` en référence vers le type d’interface `IControl`.</span><span class="sxs-lookup"><span data-stu-id="8b116-121">For example, the implementation of `IControl.Paint` provided by the previous EditBox class can only be invoked by first converting the `EditBox` reference to the `IControl` interface type.</span></span>

[!code-csharp[InterfacesFive](../../../samples/snippets/csharp/tour/interfaces/Program.cs#L71-L74)]

>[!div class="step-by-step"]
><span data-ttu-id="8b116-122">[Suivant précédent](arrays.md)
>[Next](delegates.md)</span><span class="sxs-lookup"><span data-stu-id="8b116-122">[Previous](arrays.md)
[Next](delegates.md)</span></span>
