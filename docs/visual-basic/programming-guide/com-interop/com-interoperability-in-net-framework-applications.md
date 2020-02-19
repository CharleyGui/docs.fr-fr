---
title: Interopérabilité COM dans les applications .NET Framework
ms.date: 07/20/2015
helpviewer_keywords:
- interoperability, COM and .NET Framework objects
- COM interop [Visual Basic]
- shared components
ms.assetid: f5a72143-c268-4dff-a019-974ad940e17d
ms.openlocfilehash: c3567464616d3b0b3f91ff57e8a169aca046c866
ms.sourcegitcommit: 700ea803fb06c5ce98de017c7f76463ba33ff4a9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/19/2020
ms.locfileid: "77452290"
---
# <a name="com-interoperability-in-net-framework-applications-visual-basic"></a>Interopérabilité COM dans les applications .NET Framework (Visual Basic)

Lorsque vous souhaitez utiliser des objets COM et des objets .NET Framework dans la même application, vous devez résoudre les différences dans la façon dont les objets existent en mémoire. Un objet .NET Framework se trouve dans la mémoire managée (la mémoire contrôlée par le common language runtime) et peut être déplacé par le runtime en fonction des besoins. Un objet COM se trouve dans la mémoire non managée et n’est pas censé se déplacer vers un autre emplacement de mémoire. Visual Studio et le .NET Framework fournissent des outils pour contrôler l’interaction de ces composants managés et non managés. Pour plus d’informations sur le code managé, consultez [Common Language Runtime](../../../standard/clr.md).

Outre l’utilisation d’objets COM dans les applications .NET, vous pouvez également utiliser Visual Basic pour développer des objets accessibles à partir de code non managé via COM.

Les liens de cette page fournissent des détails sur les interactions entre les objets COM et .NET Framework.

## <a name="related-sections"></a>Sections connexes

| | |
|---------|---------|
| [COM Interop](../../../visual-basic/programming-guide/com-interop/index.md) | Fournit des liens vers les rubriques qui décrivent l’interopérabilité COM dans Visual Basic, y compris les objets COM, les contrôles ActiveX, les dll Win32, les objets managés et l’héritage d’objets COM. |
| [Interopération avec du code non managé](../../../framework/interop/index.md) | Décrit brièvement certains des problèmes d’interaction entre le code managé et le code non managé, et fournit des liens pour approfondir l’étude. |
| [Wrappers COM](../../../standard/native-interop/com-wrappers.md) | Traite des wrappers pouvant être appelés par le runtime, qui permettent au code managé d’appeler des méthodes COM et des wrappers CCW (COM Callable Wrapper), qui permettent aux clients COM d’appeler des méthodes d’objet .NET. |
| [Interopérabilité COM avancée](../../../framework/interop/index.md) | Fournit des liens vers les rubriques qui décrivent l’interopérabilité COM en ce qui concerne les wrappers, les exceptions, l’héritage, les threads, les événements, les conversions et le marshaling. |
| [Tlbimp.exe (importateur de bibliothèques de types)](../../../framework/tools/tlbimp-exe-type-library-importer.md) | Présente l’outil que vous pouvez utiliser pour convertir les définitions de types trouvées dans une bibliothèque de types COM en définitions équivalentes dans un assembly common language runtime. |
