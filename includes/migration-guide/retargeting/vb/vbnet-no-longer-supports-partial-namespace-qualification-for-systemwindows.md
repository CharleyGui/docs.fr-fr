---
ms.openlocfilehash: cef8096c971da8ae245ff974697022f350cb9195
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85616050"
---
### <a name="vbnet-no-longer-supports-partial-namespace-qualification-for-systemwindows-apis"></a>VB.NET ne prend plus en charge la qualification partielle des espaces de noms pour les API System.Windows

#### <a name="details"></a>Détails

À compter de .NET Framework 4.5.2, les projets VB.NET ne peuvent plus spécifier d’API System.Windows avec des espaces de noms partiellement qualifiés. Par exemple, la référence à `Windows.Forms.DialogResult` échoue. Le code doit référencer le nom qualifié complet (<xref:System.Windows.Forms.DialogResult>) ou importer l’espace de noms et référencer <xref:System.Windows.Forms.DialogResult?displayProperty=fullName>.

#### <a name="suggestion"></a>Suggestion

Le code doit être mis à jour pour référencer les API `System.Windows` avec des noms simples (en important l’espace de noms nécessaire) ou avec des noms qualifiés complets.

| Nom    | Valeur       |
|:--------|:------------|
| Étendue   | Secondaire       |
| Version | 4.5.2       |
| Type    | Reciblage |
