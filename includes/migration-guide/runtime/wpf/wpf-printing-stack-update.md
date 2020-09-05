---
ms.openlocfilehash: e42bce91afab68e509cb35a8992fa3ca2f096872
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/05/2020
ms.locfileid: "89496154"
---
### <a name="wpf-printing-stack-update"></a>Mise à jour de la pile d’impression WPF

#### <a name="details"></a>Détails

Les API d’impression de WPF utilisant <xref:System.Printing.PrintQueue?displayProperty=fullName> appellent l’API Print Document Package de Windows au lieu de l’API d’impression XPS, qui est maintenant dépréciée. Le changement a été fait pour des raisons de maintenance : ni les utilisateurs ni les développeurs ne devraient voir de changements de comportement ou d’utilisation de l’API. La nouvelle pile d’impression est activée par défaut lors de l’exécution dans Windows 10 Creators Update. L’ancienne pile d’impression continue de fonctionner comme avant sur les versions antérieures de Windows.

#### <a name="suggestion"></a>Suggestion

Pour utiliser l’ancienne pile dans Windows 10 Creators Update, définissez la valeur REG_DWORD <code>UseXpsOMPrinting</code> de la clé de Registre <code>HKEY_CURRENT_USER\Software\Microsoft\.NETFramework\Windows Presentation Foundation\Printing</code> sur <code>1</code>.

| Name    | Valeur       |
|:--------|:------------|
| Étendue   |Edge|
|Version|4,7|
|Type|Runtime|

#### <a name="affected-apis"></a>API affectées

Non détectable via l’analyse des API.

<!--

#### Affected APIs

Not detectable via API analysis.

-->
