---
ms.openlocfilehash: cb9305f623044233082286863d2f2d2c7e9d665a
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/05/2020
ms.locfileid: "89497574"
---
### <a name="workflow-sql-persistence-adds-primary-key-clusters-and-disallows-null-values-in-some-columns"></a><span data-ttu-id="89702-101">La persistance des workflows SQL ajoute des clusters de clé primaire et interdit les valeurs null dans certaines colonnes</span><span class="sxs-lookup"><span data-stu-id="89702-101">Workflow SQL persistence adds primary key clusters and disallows null values in some columns</span></span>

#### <a name="details"></a><span data-ttu-id="89702-102">Détails</span><span class="sxs-lookup"><span data-stu-id="89702-102">Details</span></span>

<span data-ttu-id="89702-103">À compter de .NET Framework 4.7, les tables créées pour le magasin d’instances de workflow SQL par le script SqlWorkflowInstanceStoreSchema.sql utilisent des clés primaires en cluster.</span><span class="sxs-lookup"><span data-stu-id="89702-103">Starting with the .NET Framework 4.7, the tables created for the SQL Workflow Instance Store (SWIS) by the SqlWorkflowInstanceStoreSchema.sql script use clustered primary keys.</span></span> <span data-ttu-id="89702-104">Pour cette raison, les identités ne prennent pas en charge les valeurs <code>null</code>.</span><span class="sxs-lookup"><span data-stu-id="89702-104">Because of this, identities do not support <code>null</code> values.</span></span> <span data-ttu-id="89702-105">Le fonctionnement du magasin d’instances de workflow SQL n’est pas impacté par ce changement.</span><span class="sxs-lookup"><span data-stu-id="89702-105">The operation of SWIS is not impacted by this change.</span></span> <span data-ttu-id="89702-106">Les mises à jour ont été apportées pour prendre en charge la réplication transactionnelle de SQL Server.</span><span class="sxs-lookup"><span data-stu-id="89702-106">The updates were made to support SQL Server Transactional Replication.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="89702-107">Suggestion</span><span class="sxs-lookup"><span data-stu-id="89702-107">Suggestion</span></span>

<span data-ttu-id="89702-108">Le fichier SQL SqlWorkflowInstanceStoreSchemaUpgrade.sql doit être appliqué aux installations existantes pour bénéficier de ce changement.</span><span class="sxs-lookup"><span data-stu-id="89702-108">The SQL file SqlWorkflowInstanceStoreSchemaUpgrade.sql must be applied to existing installations in order to experience this change.</span></span> <span data-ttu-id="89702-109">Les nouvelles installations de base de données ont automatiquement ce changement.</span><span class="sxs-lookup"><span data-stu-id="89702-109">New database installations will automatically have the change.</span></span>

| <span data-ttu-id="89702-110">Name</span><span class="sxs-lookup"><span data-stu-id="89702-110">Name</span></span>    | <span data-ttu-id="89702-111">Valeur</span><span class="sxs-lookup"><span data-stu-id="89702-111">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="89702-112">Étendue</span><span class="sxs-lookup"><span data-stu-id="89702-112">Scope</span></span>   |<span data-ttu-id="89702-113">Edge</span><span class="sxs-lookup"><span data-stu-id="89702-113">Edge</span></span>|
|<span data-ttu-id="89702-114">Version</span><span class="sxs-lookup"><span data-stu-id="89702-114">Version</span></span>|<span data-ttu-id="89702-115">4,7</span><span class="sxs-lookup"><span data-stu-id="89702-115">4.7</span></span>|
|<span data-ttu-id="89702-116">Type</span><span class="sxs-lookup"><span data-stu-id="89702-116">Type</span></span>|<span data-ttu-id="89702-117">Runtime</span><span class="sxs-lookup"><span data-stu-id="89702-117">Runtime</span></span>|

#### <a name="affected-apis"></a><span data-ttu-id="89702-118">API affectées</span><span class="sxs-lookup"><span data-stu-id="89702-118">Affected APIs</span></span>

<span data-ttu-id="89702-119">Non détectable via l’analyse des API.</span><span class="sxs-lookup"><span data-stu-id="89702-119">Not detectable via API analysis.</span></span>

<!--

#### Affected APIs

Not detectable via API analysis.

-->
