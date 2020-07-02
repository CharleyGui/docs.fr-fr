---
ms.openlocfilehash: 5c949b79eefa68ea6f8d4ad27c716c438e24f170
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85619961"
---
### <a name="deserialization-of-objects-across-appdomains-can-fail"></a>La désérialisation d’objets entre les domaines d’application peut échouer

#### <a name="details"></a>Détails

Dans certains cas, quand une application utilise deux domaines d'application ou plus avec des bases d'application différentes, une tentative de désérialisation des objets dans le contexte d'appel logique entre les domaines d'application lève une exception.

#### <a name="suggestion"></a>Suggestion

Consultez [Atténuation : désérialisation des objets entre les domaines d’application](~/docs/framework/migration-guide/mitigation-deserialization-of-objects-across-app-domains.md)

| Nom    | Valeur       |
|:--------|:------------|
| Étendue   |Edge|
|Version|4.5.1|
|Type|Runtime|
