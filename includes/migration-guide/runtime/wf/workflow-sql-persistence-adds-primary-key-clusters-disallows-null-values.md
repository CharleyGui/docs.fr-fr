---
ms.openlocfilehash: 566a3e0455b30e901b09be88b4256ffe67bdc2b5
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/15/2020
ms.locfileid: "67802474"
---
### <a name="workflow-sql-persistence-adds-primary-key-clusters-and-disallows-null-values-in-some-columns"></a>La persistance des workflows SQL ajoute des clusters de clé primaire et interdit les valeurs null dans certaines colonnes

|   |   |
|---|---|
|Détails|À compter de .NET Framework 4.7, les tables créées pour le magasin d’instances de workflow SQL par le script SqlWorkflowInstanceStoreSchema.sql utilisent des clés primaires en cluster. Pour cette raison, les identités ne prennent pas en charge les valeurs <code>null</code>. Le fonctionnement du magasin d’instances de workflow SQL n’est pas impacté par ce changement. Les mises à jour ont été apportées pour prendre en charge la réplication transactionnelle de SQL Server.|
|Suggestion|Le fichier SQL SqlWorkflowInstanceStoreSchemaUpgrade.sql doit être appliqué aux installations existantes pour bénéficier de ce changement. Les nouvelles installations de base de données ont automatiquement ce changement.|
|Étendue|Edge|
|Version|4,7|
|Type|Runtime|
