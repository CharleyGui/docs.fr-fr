---
title: Interfaces C# - Visite guidée du langage C#
description: Les interfaces définissent des contrats implémentés par les types en C#
ms.date: 02/27/2020
ms.assetid: a9bf82f4-efd1-4216-bd34-4ef0fa48c968
ms.openlocfilehash: 62d94462fa481379cf70d63a598deb7f36be204f
ms.sourcegitcommit: 00aa62e2f469c2272a457b04e66b4cc3c97a800b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/28/2020
ms.locfileid: "78159128"
---
# <a name="interfaces"></a>Interfaces

Une ***interface*** définit un contrat qui peut être implémenté par des classes et des structs. Une interface peut contenir des méthodes, des propriétés, des événements et des indexeurs. Une interface ne fournit pas d’implémentations des membres qu’elle définit ; elle spécifie simplement les membres qui doivent être fournis par les classes ou les structs qui implémentent l’interface.

Les interfaces peuvent utiliser ***l’héritage multiple***. Dans l’exemple suivant, l’interface `IComboBox` hérite à la fois de `ITextBox` et `IListBox`.

[!code-csharp[InterfacesOne](../../../samples/snippets/csharp/tour/interfaces/Program.cs#L5-L17)]

Les classes et les structs peuvent implémenter plusieurs interfaces. Dans l’exemple suivant, la classe `EditBox` implémente à la fois `IControl` et `IDataBound`.

[!code-csharp[InterfacesTwo](../../../samples/snippets/csharp/tour/interfaces/Program.cs#L19-L27)]

Lorsqu’une classe ou un struct implémente une interface spécifique, les instances de cette classe ou struct peuvent être converties implicitement en ce type d’interface. Par exemple

[!code-csharp[InterfacesThree](../../../samples/snippets/csharp/tour/interfaces/Program.cs#L33-L35)]

Dans les cas où une instance n’est pas statiquement connue pour implémenter une interface particulière, les casts de type dynamique peuvent être utilisés. Par exemple, les instructions suivantes utilisent des casts de type dynamiques pour obtenir les implémentations des interfaces `IControl` et `IDataBound` d’un objet. Étant donné que le type réel au moment de l’exécution de l’objet est `EditBox`, les casts réussissent.

[!code-csharp[InterfacesFour](../../../samples/snippets/csharp/tour/interfaces/Program.cs#L40-L42)]

Dans la classe `EditBox` précédente, la méthode `Paint` de l’interface `IControl` et la méthode `Bind` de l’interface `IDataBound` sont implémentées à l’aide des membres publics. C# prend également en charge les ***implémentations de membres d’interface*** explicites, permettant ainsi à la classe ou structure d’éviter d’avoir à créer des membres publics. Une implémentation de membre d’interface explicite est écrite à l’aide du nom de membre d’interface qualifié complet. Par exemple, la classe `EditBox` peut implémenter les méthodes `IControl.Paint` et `IDataBound.Bind` à l’aide des implémentations de membres d’interface explicites, comme suit.

[!code-csharp[InterfacesFive](../../../samples/snippets/csharp/tour/interfaces/Program.cs#L60-L64)]

Les membres d’interface explicites sont accessibles uniquement via le type interface. Par exemple, l’implémentation de `IControl.Paint` fournie par la classe EditBox précédente ne peut être appelée en convertissant d’abord l’ `EditBox` en référence vers le type d’interface `IControl`.

[!code-csharp[InterfacesFive](../../../samples/snippets/csharp/tour/interfaces/Program.cs#L71-L74)]

>[!div class="step-by-step"]
>[Précédent](arrays.md)
>[Suivant](delegates.md)
