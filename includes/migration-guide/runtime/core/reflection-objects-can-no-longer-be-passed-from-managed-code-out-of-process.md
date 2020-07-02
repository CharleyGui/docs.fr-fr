---
ms.openlocfilehash: a54b17b2002bd0f85b8b47c5e37e040470d6c494
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85621335"
---
### <a name="reflection-objects-can-no-longer-be-passed-from-managed-code-to-out-of-process-dcom-clients"></a>Les objets de réflexion ne peuvent plus être passés du code managé aux clients DCOM hors processus

#### <a name="details"></a>Détails

Les objets de réflexion ne peuvent plus être passés du code managé aux clients DCOM hors processus. Les types suivants sont concernés :<ul><li><xref:System.Reflection.Assembly?displayProperty=fullName></li><li><xref:System.Reflection.MemberInfo?displayProperty=fullName> (et ses types dérivés, dont <xref:System.Reflection.FieldInfo?displayProperty=fullName>, <xref:System.Reflection.MethodInfo?displayProperty=fullName>, <xref:System.Type?displayProperty=fullName> et <xref:System.Reflection.TypeInfo?displayProperty=fullName>)</li><li><xref:System.Reflection.MethodBody?displayProperty=fullName></li><li><xref:System.Reflection.Module?displayProperty=fullName></li><li><xref:System.Reflection.ParameterInfo?displayProperty=fullName>.</li></ul>Les appels à <code>IMarshal</code> pour l’objet retournent <code>E_NOINTERFACE</code>.

#### <a name="suggestion"></a>Suggestion

Mettez à jour le code de marshaling pour utiliser des objets autres que des objets de réflexion.

| Nom    | Valeur       |
|:--------|:------------|
| Étendue   |Secondaire|
|Version|4.6|
|Type|Runtime|
