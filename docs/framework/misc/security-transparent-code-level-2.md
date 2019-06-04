---
title: Code transparent de sécurité, niveau 2
ms.date: 03/30/2017
helpviewer_keywords:
- transparency
- level 2 transparency
- security-transparent code
- security-critical code
ms.assetid: 4d05610a-0da6-4f08-acea-d54c9d6143c0
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 36c3f139564b39555370cd5d41133f39c6b271bb
ms.sourcegitcommit: 155012a8a826ee8ab6aa49b1b3a3b532e7b7d9bd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2019
ms.locfileid: "66487831"
---
# <a name="security-transparent-code-level-2"></a><span data-ttu-id="68907-102">Code transparent de sécurité, niveau 2</span><span class="sxs-lookup"><span data-stu-id="68907-102">Security-Transparent Code, Level 2</span></span>

<a name="top"></a>

[!INCLUDE[net_security_note](../../../includes/net-security-note-md.md)]

<span data-ttu-id="68907-103">Transparence de niveau 2 a été introduite dans le .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="68907-103">Level 2 transparency was introduced in the .NET Framework 4.</span></span> <span data-ttu-id="68907-104">Les trois principes de ce modèle sont le code transparent, le code critique sécurisé et le code critique de sécurité.</span><span class="sxs-lookup"><span data-stu-id="68907-104">The three tenets of this model are transparent code, security-safe-critical code, and security-critical code.</span></span>

- <span data-ttu-id="68907-105">Le code transparent, y compris le code qui s'exécute en mode confiance totale, peut appeler d'autre code transparent ou code critique sécurisé uniquement.</span><span class="sxs-lookup"><span data-stu-id="68907-105">Transparent code, including code that is running as full trust, can call other transparent code or security-safe-critical code only.</span></span> <span data-ttu-id="68907-106">Il ne peut effectuer que les actions autorisées par le jeu d'autorisations de confiance partielle du domaine (s'il en existe un).</span><span class="sxs-lookup"><span data-stu-id="68907-106">It can only perform actions allowed by the domain’s partial trust permission set (if one exists).</span></span> <span data-ttu-id="68907-107">Voici ce que le code transparent ne peut pas faire :</span><span class="sxs-lookup"><span data-stu-id="68907-107">Transparent code cannot do the following:</span></span>

  - <span data-ttu-id="68907-108">exécuter un <xref:System.Security.CodeAccessPermission.Assert%2A> ou une élévation de privilège ;</span><span class="sxs-lookup"><span data-stu-id="68907-108">Perform an <xref:System.Security.CodeAccessPermission.Assert%2A> or elevation of privilege.</span></span>

  - <span data-ttu-id="68907-109">contenir du code non sécurisé ou non vérifiable ;</span><span class="sxs-lookup"><span data-stu-id="68907-109">Contain unsafe or unverifiable code.</span></span>

  - <span data-ttu-id="68907-110">appeler directement du code critique ;</span><span class="sxs-lookup"><span data-stu-id="68907-110">Directly call critical code.</span></span>

  - <span data-ttu-id="68907-111">appeler du code natif ou du code possédant l'attribut <xref:System.Security.SuppressUnmanagedCodeSecurityAttribute> ;</span><span class="sxs-lookup"><span data-stu-id="68907-111">Call native code or code with the <xref:System.Security.SuppressUnmanagedCodeSecurityAttribute> attribute.</span></span>

  - <span data-ttu-id="68907-112">appeler un membre protégé par un <xref:System.Security.Permissions.SecurityAction.LinkDemand> ;</span><span class="sxs-lookup"><span data-stu-id="68907-112">Call a member that is protected by a <xref:System.Security.Permissions.SecurityAction.LinkDemand>.</span></span>

  - <span data-ttu-id="68907-113">hériter de types critiques.</span><span class="sxs-lookup"><span data-stu-id="68907-113">Inherit from critical types.</span></span>

  <span data-ttu-id="68907-114">Par ailleurs, les méthodes transparentes ne peuvent pas substituer des méthodes virtuelles critiques ni implémenter des méthodes d'interface critiques.</span><span class="sxs-lookup"><span data-stu-id="68907-114">In addition, transparent methods cannot override critical virtual methods or implement critical interface methods.</span></span>

- <span data-ttu-id="68907-115">Le code critique sécurisé est entièrement fiable, mais peut être appelé par du code transparent.</span><span class="sxs-lookup"><span data-stu-id="68907-115">Safe-critical code is fully trusted but is callable by transparent code.</span></span> <span data-ttu-id="68907-116">Il expose une surface limitée de code de confiance totale ; des vérifications d'exactitude et de sécurité s'opèrent dans le code critique sécurisé.</span><span class="sxs-lookup"><span data-stu-id="68907-116">It exposes a limited surface area of full-trust code; correctness and security verifications happen in safe-critical code.</span></span>

- <span data-ttu-id="68907-117">Le code critique de sécurité peut appeler n'importe quel code et bénéficie d'un niveau de confiance totale, mais il ne peut pas être appelé par du code transparent.</span><span class="sxs-lookup"><span data-stu-id="68907-117">Security-critical code can call any code and is fully trusted, but it cannot be called by transparent code.</span></span>

<span data-ttu-id="68907-118">Cette rubrique contient les sections suivantes :</span><span class="sxs-lookup"><span data-stu-id="68907-118">This topic contains the following sections:</span></span>

- [<span data-ttu-id="68907-119">Exemples d’utilisation et de comportements</span><span class="sxs-lookup"><span data-stu-id="68907-119">Usage Examples and Behaviors</span></span>](#examples)

- [<span data-ttu-id="68907-120">Modèles de substitution</span><span class="sxs-lookup"><span data-stu-id="68907-120">Override Patterns</span></span>](#override)

- [<span data-ttu-id="68907-121">Règles d’héritage</span><span class="sxs-lookup"><span data-stu-id="68907-121">Inheritance Rules</span></span>](#inheritance)

- [<span data-ttu-id="68907-122">Règles et des informations supplémentaires</span><span class="sxs-lookup"><span data-stu-id="68907-122">Additional Information and Rules</span></span>](#additional)

<a name="examples"></a>

## <a name="usage-examples-and-behaviors"></a><span data-ttu-id="68907-123">Exemples d'utilisation et comportements</span><span class="sxs-lookup"><span data-stu-id="68907-123">Usage Examples and Behaviors</span></span>

<span data-ttu-id="68907-124">Pour spécifier les règles de .NET Framework 4 (transparence de niveau 2), utilisez l’annotation suivante pour un assembly :</span><span class="sxs-lookup"><span data-stu-id="68907-124">To specify .NET Framework 4 rules (level 2 transparency), use the following annotation for an assembly:</span></span>

```csharp
[assembly: SecurityRules(SecurityRuleSet.Level2)]
```

<span data-ttu-id="68907-125">Pour verrouiller les règles du .NET Framework 2.0 (transparence de niveau 1), utilisez l'annotation suivante :</span><span class="sxs-lookup"><span data-stu-id="68907-125">To lock into the .NET Framework 2.0 rules (level 1 transparency), use the following annotation:</span></span>

```csharp
[assembly: SecurityRules(SecurityRuleSet.Level1)]
```

<span data-ttu-id="68907-126">Si vous n’annotez pas un assembly, les règles de .NET Framework 4 sont utilisées par défaut.</span><span class="sxs-lookup"><span data-stu-id="68907-126">If you do not annotate an assembly, the .NET Framework 4 rules are used by default.</span></span> <span data-ttu-id="68907-127">Toutefois, la meilleure pratique recommandée consiste à utiliser le <xref:System.Security.SecurityRulesAttribute> au lieu de selon la valeur par défaut.</span><span class="sxs-lookup"><span data-stu-id="68907-127">However, the recommended best practice is to use the <xref:System.Security.SecurityRulesAttribute> attribute instead of depending on the default.</span></span>

### <a name="assembly-wide-annotation"></a><span data-ttu-id="68907-128">Annotation à l'échelle de l'assembly</span><span class="sxs-lookup"><span data-stu-id="68907-128">Assembly-wide Annotation</span></span>

<span data-ttu-id="68907-129">Les règles suivantes s'appliquent à l'utilisation d'attributs au niveau de l'assembly :</span><span class="sxs-lookup"><span data-stu-id="68907-129">The following rules apply to the use of attributes at the assembly level:</span></span>

- <span data-ttu-id="68907-130">Aucun attribut : Si vous ne spécifiez pas de tous les attributs, le runtime interprète tout le code comme critique de sécurité, à l’exception où être critique de sécurité ne respecte pas une règle d’héritage (par exemple, en cas de substitution ou de mise en œuvre un transparent virtuel ou méthode d’interface).</span><span class="sxs-lookup"><span data-stu-id="68907-130">No attributes: If you do not specify any attributes, the runtime interprets all code as security-critical, except where being security-critical violates an inheritance rule (for example, when overriding or implementing a transparent virtual or interface method).</span></span> <span data-ttu-id="68907-131">Dans ces cas de figure, les méthodes sont critiques sécurisées.</span><span class="sxs-lookup"><span data-stu-id="68907-131">In those cases, the methods are safe-critical.</span></span> <span data-ttu-id="68907-132">Si vous ne spécifiez aucun attribut, le common language runtime détermine les règles de transparence à votre place.</span><span class="sxs-lookup"><span data-stu-id="68907-132">Specifying no attribute causes the common language runtime to determine the transparency rules for you.</span></span>

- <span data-ttu-id="68907-133">`SecurityTransparent`: Tout le code est transparent. la totalité de l’assembly ne fait rien de privilégié ou unsafe.</span><span class="sxs-lookup"><span data-stu-id="68907-133">`SecurityTransparent`: All code is transparent; the entire assembly will not do anything privileged or unsafe.</span></span>

- <span data-ttu-id="68907-134">`SecurityCritical`: Tout le code introduit par des types dans cet assembly est critique ; le reste du code est transparent.</span><span class="sxs-lookup"><span data-stu-id="68907-134">`SecurityCritical`: All code that is introduced by types in this assembly is critical; all other code is transparent.</span></span> <span data-ttu-id="68907-135">Ce scénario équivaut à ne spécifier aucun attribut ; cependant, le common language runtime ne détermine pas automatiquement les règles de transparence.</span><span class="sxs-lookup"><span data-stu-id="68907-135">This scenario is similar to not specifying any attributes; however, the common language runtime does not automatically determine the transparency rules.</span></span> <span data-ttu-id="68907-136">Par exemple, si vous substituez une méthode virtuelle ou abstraite ou que vous implémentez une méthode d'interface, par défaut, cette méthode est transparente.</span><span class="sxs-lookup"><span data-stu-id="68907-136">For example, if you override a virtual or abstract method or implement an interface method, by default, that method is transparent.</span></span> <span data-ttu-id="68907-137">Vous devez annoter explicitement la méthode comme étant `SecurityCritical` ou `SecuritySafeCritical` ; sinon, une exception <xref:System.TypeLoadException> est levée au moment du chargement.</span><span class="sxs-lookup"><span data-stu-id="68907-137">You must explicitly annotate the method as `SecurityCritical` or `SecuritySafeCritical`; otherwise, a <xref:System.TypeLoadException> will be thrown at load time.</span></span> <span data-ttu-id="68907-138">Cette règle vaut aussi quand la classe de base et la classe dérivée se trouvent dans le même assembly.</span><span class="sxs-lookup"><span data-stu-id="68907-138">This rule also applies when both the base class and the derived class are in the same assembly.</span></span>

- <span data-ttu-id="68907-139">`AllowPartiallyTrustedCallers` (niveau 2 uniquement) : Tout le code est transparent par défaut.</span><span class="sxs-lookup"><span data-stu-id="68907-139">`AllowPartiallyTrustedCallers` (level 2 only): All code defaults to transparent.</span></span> <span data-ttu-id="68907-140">Cependant, chaque type et membre individuel peut avoir d'autres attributs.</span><span class="sxs-lookup"><span data-stu-id="68907-140">However, individual types and members can have other attributes.</span></span>

<span data-ttu-id="68907-141">Le tableau suivant compare le comportement de niveau assembly pour le niveau 2 avec le niveau 1.</span><span class="sxs-lookup"><span data-stu-id="68907-141">The following table compares the assembly level behavior for Level 2 with Level 1.</span></span>

|<span data-ttu-id="68907-142">Assembly (attribut)</span><span class="sxs-lookup"><span data-stu-id="68907-142">Assembly attribute</span></span>|<span data-ttu-id="68907-143">Niveau 2</span><span class="sxs-lookup"><span data-stu-id="68907-143">Level 2</span></span>|<span data-ttu-id="68907-144">Niveau 1</span><span class="sxs-lookup"><span data-stu-id="68907-144">Level 1</span></span>|
|------------------------|-------------|-------------|
|<span data-ttu-id="68907-145">Aucun attribut sur un assembly de niveau de confiance partielle</span><span class="sxs-lookup"><span data-stu-id="68907-145">No attribute on a partially trusted assembly</span></span>|<span data-ttu-id="68907-146">Les types et les membres sont transparents par défaut, mais peuvent être critiques de sécurité ou critiques sécurisés.</span><span class="sxs-lookup"><span data-stu-id="68907-146">Types and members are by default transparent, but can be security-critical or security-safe-critical.</span></span>|<span data-ttu-id="68907-147">Tous les types et membres sont transparents.</span><span class="sxs-lookup"><span data-stu-id="68907-147">All types and members are transparent.</span></span>|
|<span data-ttu-id="68907-148">Aucun attribut</span><span class="sxs-lookup"><span data-stu-id="68907-148">No attribute</span></span>|<span data-ttu-id="68907-149">Si vous ne spécifiez aucun attribut, le common language runtime détermine les règles de transparence à votre place.</span><span class="sxs-lookup"><span data-stu-id="68907-149">Specifying no attribute causes the common language runtime to determine the transparency rules for you.</span></span> <span data-ttu-id="68907-150">Tous les types et membres sont critiques de sécurité, sauf si le fait d'être critique de sécurité va à l'encontre d'une règle d'héritage.</span><span class="sxs-lookup"><span data-stu-id="68907-150">All types and members are security-critical, except where being security-critical violates an inheritance rule.</span></span>|<span data-ttu-id="68907-151">Sur un assembly d'un niveau de confiance totale (dans le Global Assembly Cache ou s'il est identifié comme étant entièrement fiable dans le `AppDomain`) tous les types sont transparents et tous les membres sont critiques sécurisés.</span><span class="sxs-lookup"><span data-stu-id="68907-151">On a fully trusted assembly (in the global assembly cache or identified as full trust in the `AppDomain`) all types are transparent and all members are security-safe-critical.</span></span>|
|`SecurityTransparent`|<span data-ttu-id="68907-152">Tous les types et membres sont transparents.</span><span class="sxs-lookup"><span data-stu-id="68907-152">All types and members are transparent.</span></span>|<span data-ttu-id="68907-153">Tous les types et membres sont transparents.</span><span class="sxs-lookup"><span data-stu-id="68907-153">All types and members are transparent.</span></span>|
|`SecurityCritical(SecurityCriticalScope.Everything)`|<span data-ttu-id="68907-154">Non applicable.</span><span class="sxs-lookup"><span data-stu-id="68907-154">Not applicable.</span></span>|<span data-ttu-id="68907-155">Tous les types et membres sont critiques de sécurité.</span><span class="sxs-lookup"><span data-stu-id="68907-155">All types and members are security-critical.</span></span>|
|`SecurityCritical`|<span data-ttu-id="68907-156">Tout le code introduit par des types dans cet assembly est critique ; le reste du code est transparent.</span><span class="sxs-lookup"><span data-stu-id="68907-156">All code that is introduced by types in this assembly is critical; all other code is transparent.</span></span> <span data-ttu-id="68907-157">Si vous substituez une méthode virtuelle ou abstraite ou que vous implémentez une méthode d'interface, vous devez annoter explicitement la méthode comme étant `SecurityCritical` ou `SecuritySafeCritical`.</span><span class="sxs-lookup"><span data-stu-id="68907-157">If you override a virtual or abstract method or implement an interface method, you must explicitly annotate the method as `SecurityCritical` or `SecuritySafeCritical`.</span></span>|<span data-ttu-id="68907-158">Tout le code est transparent par défaut.</span><span class="sxs-lookup"><span data-stu-id="68907-158">All code defaults to transparent.</span></span> <span data-ttu-id="68907-159">Cependant, chaque type et membre individuel peut avoir d'autres attributs.</span><span class="sxs-lookup"><span data-stu-id="68907-159">However, individual types and members can have other attributes.</span></span>|

### <a name="type-and-member-annotation"></a><span data-ttu-id="68907-160">Annotation de type et de membre</span><span class="sxs-lookup"><span data-stu-id="68907-160">Type and Member Annotation</span></span>

<span data-ttu-id="68907-161">Les attributs de sécurité qui s'appliquent à un type s'appliquent aussi aux membres introduits par ce type.</span><span class="sxs-lookup"><span data-stu-id="68907-161">The security attributes that are applied to a type also apply to the members that are introduced by the type.</span></span> <span data-ttu-id="68907-162">En revanche, ils ne s'appliquent pas aux substitutions virtuelles ou abstraites des implémentations de classe ou d'interface de base.</span><span class="sxs-lookup"><span data-stu-id="68907-162">However, they do not apply to virtual or abstract overrides of the base class or interface implementations.</span></span> <span data-ttu-id="68907-163">L'utilisation d'attributs au niveau du type et du membre obéit aux règles suivantes :</span><span class="sxs-lookup"><span data-stu-id="68907-163">The following rules apply to the use of attributes at the type and member level:</span></span>

- <span data-ttu-id="68907-164">`SecurityCritical`: Le type ou le membre est critique et peut être appelée uniquement par le code de confiance totale.</span><span class="sxs-lookup"><span data-stu-id="68907-164">`SecurityCritical`: The type or member is critical and can be called only by full-trust code.</span></span> <span data-ttu-id="68907-165">Les méthodes introduites dans un type critique de sécurité sont critiques.</span><span class="sxs-lookup"><span data-stu-id="68907-165">Methods that are introduced in a security-critical type are critical.</span></span>

    > [!IMPORTANT]
    > <span data-ttu-id="68907-166">Les méthodes virtuelles et abstraites introduites dans des classes ou interfaces de base et substituées ou implémentées dans une classe critique de sécurité sont transparentes par défaut.</span><span class="sxs-lookup"><span data-stu-id="68907-166">Virtual and abstract methods that are introduced in base classes or interfaces, and overridden or implemented in a security-critical class are transparent by default.</span></span> <span data-ttu-id="68907-167">Elles doivent être identifiées comme étant `SecuritySafeCritical` ou `SecurityCritical`.</span><span class="sxs-lookup"><span data-stu-id="68907-167">They must be identified as either `SecuritySafeCritical` or `SecurityCritical`.</span></span>

- <span data-ttu-id="68907-168">`SecuritySafeCritical`: Le type ou le membre est critique sécurisé.</span><span class="sxs-lookup"><span data-stu-id="68907-168">`SecuritySafeCritical`: The type or member is safe-critical.</span></span> <span data-ttu-id="68907-169">Cependant, le type ou le membre peut être appelé à partir d'un code transparent (de niveau de confiance partielle) et a les mêmes capacités que n'importe quel autre code critique.</span><span class="sxs-lookup"><span data-stu-id="68907-169">However, the type or member can be called from transparent (partially trusted) code and is as capable as any other critical code.</span></span> <span data-ttu-id="68907-170">La sécurité du code doit faire l'objet d'un audit.</span><span class="sxs-lookup"><span data-stu-id="68907-170">The code must be audited for security.</span></span>

[<span data-ttu-id="68907-171">Retour au début</span><span class="sxs-lookup"><span data-stu-id="68907-171">Back to top</span></span>](#top)

<a name="override"></a>

## <a name="override-patterns"></a><span data-ttu-id="68907-172">Modèles de substitution</span><span class="sxs-lookup"><span data-stu-id="68907-172">Override Patterns</span></span>

<span data-ttu-id="68907-173">Le tableau suivant présente les substitutions de méthodes autorisées pour la transparence de niveau 2.</span><span class="sxs-lookup"><span data-stu-id="68907-173">The following table shows the method overrides allowed for level 2 transparency.</span></span>

|<span data-ttu-id="68907-174">Membre d'interface/virtuel de base</span><span class="sxs-lookup"><span data-stu-id="68907-174">Base virtual/interface member</span></span>|<span data-ttu-id="68907-175">Substitution/interface</span><span class="sxs-lookup"><span data-stu-id="68907-175">Override/interface</span></span>|
|------------------------------------|-------------------------|
|`Transparent`|`Transparent`|
|`Transparent`|`SafeCritical`|
|`SafeCritical`|`Transparent`|
|`SafeCritical`|`SafeCritical`|
|`Critical`|`Critical`|

[<span data-ttu-id="68907-176">Retour au début</span><span class="sxs-lookup"><span data-stu-id="68907-176">Back to top</span></span>](#top)

<a name="inheritance"></a>

## <a name="inheritance-rules"></a><span data-ttu-id="68907-177">Règles d'héritage</span><span class="sxs-lookup"><span data-stu-id="68907-177">Inheritance Rules</span></span>

<span data-ttu-id="68907-178">Dans cette section, l'ordre suivant est attribué au code `Transparent`, `Critical` et `SafeCritical` en fonction de l'accès et des fonctionnalités :</span><span class="sxs-lookup"><span data-stu-id="68907-178">In this section, the following order is assigned to `Transparent`, `Critical`, and `SafeCritical` code based on access and capabilities:</span></span>

`Transparent` < `SafeCritical` < `Critical`

- <span data-ttu-id="68907-179">Règles pour les types : Allant de gauche à droite, l’accès devient plus restrictif.</span><span class="sxs-lookup"><span data-stu-id="68907-179">Rules for types: Going from left to right, access becomes more restrictive.</span></span> <span data-ttu-id="68907-180">Les types dérivés doivent être au moins aussi restrictifs que le type de base.</span><span class="sxs-lookup"><span data-stu-id="68907-180">Derived types must be at least as restrictive as the base type.</span></span>

- <span data-ttu-id="68907-181">Règles pour les méthodes : Méthodes dérivées ne peuvent pas changer l’accessibilité depuis la méthode de base.</span><span class="sxs-lookup"><span data-stu-id="68907-181">Rules for methods: Derived methods cannot change accessibility from the base method.</span></span> <span data-ttu-id="68907-182">Pour le comportement par défaut, toutes les méthodes dérivées qui ne sont pas annotées sont `Transparent`.</span><span class="sxs-lookup"><span data-stu-id="68907-182">For default behavior, all derived methods that are not annotated are `Transparent`.</span></span> <span data-ttu-id="68907-183">Les dérivés des types critiques provoquent une exception si la méthode substituée n’est pas explicitement annotée comme étant `SecurityCritical`.</span><span class="sxs-lookup"><span data-stu-id="68907-183">Derivatives of critical types cause an exception to be thrown if the overridden method is not explicitly annotated as `SecurityCritical`.</span></span>

<span data-ttu-id="68907-184">Le tableau suivant présente les modèles d'héritage de type autorisés.</span><span class="sxs-lookup"><span data-stu-id="68907-184">The following table shows the allowed type inheritance patterns.</span></span>

|<span data-ttu-id="68907-185">Classe de base</span><span class="sxs-lookup"><span data-stu-id="68907-185">Base class</span></span>|<span data-ttu-id="68907-186">La classe dérivée peut être</span><span class="sxs-lookup"><span data-stu-id="68907-186">Derived class can be</span></span>|
|----------------|--------------------------|
|`Transparent`|`Transparent`|
|`Transparent`|`SafeCritical`|
|`Transparent`|`Critical`|
|`SafeCritical`|`SafeCritical`|
|`SafeCritical`|`Critical`|
|`Critical`|`Critical`|

<span data-ttu-id="68907-187">Le tableau suivant présente les modèles d’héritage de type non autorisés.</span><span class="sxs-lookup"><span data-stu-id="68907-187">The following table shows the disallowed type inheritance patterns.</span></span>

|<span data-ttu-id="68907-188">Classe de base</span><span class="sxs-lookup"><span data-stu-id="68907-188">Base class</span></span>|<span data-ttu-id="68907-189">La classe dérivée ne peut pas être</span><span class="sxs-lookup"><span data-stu-id="68907-189">Derived class cannot be</span></span>|
|----------------|-----------------------------|
|`SafeCritical`|`Transparent`|
|`Critical`|`Transparent`|
|`Critical`|`SafeCritical`|

<span data-ttu-id="68907-190">Le tableau suivant présente les modèles d'héritage de méthode autorisés.</span><span class="sxs-lookup"><span data-stu-id="68907-190">The following table shows the allowed method inheritance patterns.</span></span>

|<span data-ttu-id="68907-191">Méthode de base</span><span class="sxs-lookup"><span data-stu-id="68907-191">Base method</span></span>|<span data-ttu-id="68907-192">La méthode dérivée peut être</span><span class="sxs-lookup"><span data-stu-id="68907-192">Derived method can be</span></span>|
|-----------------|---------------------------|
|`Transparent`|`Transparent`|
|`Transparent`|`SafeCritical`|
|`SafeCritical`|`Transparent`|
|`SafeCritical`|`SafeCritical`|
|`Critical`|`Critical`|

<span data-ttu-id="68907-193">Le tableau suivant présente les modèles d'héritage de méthode non autorisés.</span><span class="sxs-lookup"><span data-stu-id="68907-193">The following table shows the disallowed method inheritance patterns.</span></span>

|<span data-ttu-id="68907-194">Méthode de base</span><span class="sxs-lookup"><span data-stu-id="68907-194">Base method</span></span>|<span data-ttu-id="68907-195">La méthode dérivée ne peut pas être</span><span class="sxs-lookup"><span data-stu-id="68907-195">Derived method cannot be</span></span>|
|-----------------|------------------------------|
|`Transparent`|`Critical`|
|`SafeCritical`|`Critical`|
|`Critical`|`Transparent`|
|`Critical`|`SafeCritical`|

> [!NOTE]
> <span data-ttu-id="68907-196">Ces règles d'héritage s'appliquent aux types et membres de niveau 2.</span><span class="sxs-lookup"><span data-stu-id="68907-196">These inheritance rules apply to level 2 types and members.</span></span> <span data-ttu-id="68907-197">Les types contenus dans les assemblys de niveau 1 peuvent hériter des types et membres critiques de sécurité de niveau 2.</span><span class="sxs-lookup"><span data-stu-id="68907-197">Types in level 1 assemblies can inherit from level 2 security-critical types and members.</span></span> <span data-ttu-id="68907-198">Par conséquent, les types et membres de niveau 2 doivent avoir des demandes d'héritage distinctes pour les héritiers de niveau 1.</span><span class="sxs-lookup"><span data-stu-id="68907-198">Therefore, level 2 types and members must have separate inheritance demands for level 1 inheritors.</span></span>

[<span data-ttu-id="68907-199">Retour au début</span><span class="sxs-lookup"><span data-stu-id="68907-199">Back to top</span></span>](#top)

<a name="additional"></a>

## <a name="additional-information-and-rules"></a><span data-ttu-id="68907-200">Informations et règles supplémentaires</span><span class="sxs-lookup"><span data-stu-id="68907-200">Additional Information and Rules</span></span>

### <a name="linkdemand-support"></a><span data-ttu-id="68907-201">Prise en charge de LinkDemand</span><span class="sxs-lookup"><span data-stu-id="68907-201">LinkDemand Support</span></span>

<span data-ttu-id="68907-202">Le modèle de transparence de niveau 2 remplace le <xref:System.Security.Permissions.SecurityAction.LinkDemand> par l'attribut <xref:System.Security.SecurityCriticalAttribute>.</span><span class="sxs-lookup"><span data-stu-id="68907-202">The level 2 transparency model replaces the <xref:System.Security.Permissions.SecurityAction.LinkDemand> with the <xref:System.Security.SecurityCriticalAttribute> attribute.</span></span> <span data-ttu-id="68907-203">Dans le code hérité (de niveau 1), un <xref:System.Security.Permissions.SecurityAction.LinkDemand> est automatiquement traité comme un <xref:System.Security.Permissions.SecurityAction.Demand>.</span><span class="sxs-lookup"><span data-stu-id="68907-203">In legacy (level 1) code, a <xref:System.Security.Permissions.SecurityAction.LinkDemand> is automatically treated as a <xref:System.Security.Permissions.SecurityAction.Demand>.</span></span>

### <a name="reflection"></a><span data-ttu-id="68907-204">Réflexion</span><span class="sxs-lookup"><span data-stu-id="68907-204">Reflection</span></span>

<span data-ttu-id="68907-205">L'appel d'une méthode critique ou la lecture d'un champ critique déclenche une demande de confiance totale (comme si vous appeliez une méthode ou un champ privé).</span><span class="sxs-lookup"><span data-stu-id="68907-205">Invoking a critical method or reading a critical field triggers a demand for full trust (just as if you were invoking a private method or field).</span></span> <span data-ttu-id="68907-206">Autrement dit, du code de niveau de confiance totale peut appeler une méthode critique, alors que du code de niveau de confiance partielle ne le peut pas.</span><span class="sxs-lookup"><span data-stu-id="68907-206">Therefore, full-trust code can invoke a critical method, whereas partial-trust code cannot.</span></span>

<span data-ttu-id="68907-207">Les propriétés suivantes ont été ajoutées à l'espace de noms <xref:System.Reflection> pour déterminer si le type, la méthode ou le champ est `SecurityCritical`, `SecuritySafeCritical` ou `SecurityTransparent` : <xref:System.Type.IsSecurityCritical%2A>, <xref:System.Reflection.MethodBase.IsSecuritySafeCritical%2A> et <xref:System.Reflection.MethodBase.IsSecurityTransparent%2A>.</span><span class="sxs-lookup"><span data-stu-id="68907-207">The following properties have been added to the <xref:System.Reflection> namespace to determine whether the type, method, or field is `SecurityCritical`, `SecuritySafeCritical`, or `SecurityTransparent`:  <xref:System.Type.IsSecurityCritical%2A>, <xref:System.Reflection.MethodBase.IsSecuritySafeCritical%2A>, and <xref:System.Reflection.MethodBase.IsSecurityTransparent%2A>.</span></span> <span data-ttu-id="68907-208">Ces propriétés permettent de déterminer la transparence par la réflexion plutôt que par la vérification de la présence de l'attribut.</span><span class="sxs-lookup"><span data-stu-id="68907-208">Use these properties to determine transparency by using reflection instead of checking for the presence of the attribute.</span></span> <span data-ttu-id="68907-209">Compte tenu de la complexité des règles de transparence, vérifier la présence de l'attribut peut ne pas suffire.</span><span class="sxs-lookup"><span data-stu-id="68907-209">The transparency rules are complex, and checking for the attribute may not be sufficient.</span></span>

> [!NOTE]
> <span data-ttu-id="68907-210">Un `SafeCritical` retourne de la méthode `true` pour les deux <xref:System.Type.IsSecurityCritical%2A> et <xref:System.Reflection.MethodBase.IsSecuritySafeCritical%2A>, car `SafeCritical` est réellement critique (il a les mêmes fonctionnalités que le code critique, mais elle peut être appelée à partir du code transparent).</span><span class="sxs-lookup"><span data-stu-id="68907-210">A `SafeCritical` method returns `true` for both <xref:System.Type.IsSecurityCritical%2A> and <xref:System.Reflection.MethodBase.IsSecuritySafeCritical%2A>, because `SafeCritical` is indeed critical (it has the same capabilities as critical code, but it can be called from transparent code).</span></span>

<span data-ttu-id="68907-211">Les méthodes dynamiques héritent de la transparence des modules auxquels elles sont attachées ; elles n'héritent pas de la transparence du type (si elles sont attachées à un type).</span><span class="sxs-lookup"><span data-stu-id="68907-211">Dynamic methods inherit the transparency of the modules they are attached to; they do not inherit the transparency of the type (if they are attached to a type).</span></span>

### <a name="skip-verification-in-full-trust"></a><span data-ttu-id="68907-212">Ignorer la vérification en mode confiance totale</span><span class="sxs-lookup"><span data-stu-id="68907-212">Skip Verification in Full Trust</span></span>

<span data-ttu-id="68907-213">Vous pouvez ignorer la vérification pour les assemblys transparents de niveau de confiance totale en attribuant à la propriété <xref:System.Security.SecurityRulesAttribute.SkipVerificationInFullTrust%2A> la valeur `true` dans l'attribut <xref:System.Security.SecurityRulesAttribute> :</span><span class="sxs-lookup"><span data-stu-id="68907-213">You can skip verification for fully trusted transparent assemblies by setting the <xref:System.Security.SecurityRulesAttribute.SkipVerificationInFullTrust%2A> property to `true` in the <xref:System.Security.SecurityRulesAttribute> attribute:</span></span>

`[assembly: SecurityRules(SecurityRuleSet.Level2, SkipVerificationInFullTrust = true)]`

<span data-ttu-id="68907-214">La valeur par défaut de la propriété <xref:System.Security.SecurityRulesAttribute.SkipVerificationInFullTrust%2A> étant `false`, elle doit avoir la valeur `true` pour ignorer la vérification.</span><span class="sxs-lookup"><span data-stu-id="68907-214">The <xref:System.Security.SecurityRulesAttribute.SkipVerificationInFullTrust%2A> property is `false` by default, so the property must be set to `true` to skip verification.</span></span> <span data-ttu-id="68907-215">Cela doit être fait uniquement à des fins d'optimisation.</span><span class="sxs-lookup"><span data-stu-id="68907-215">This should be done for optimization purposes only.</span></span> <span data-ttu-id="68907-216">Vous devez vous assurer que le code transparent de l’assembly est vérifiable à l’aide de la `transparent` option dans le [outil PEVerify](../../../docs/framework/tools/peverify-exe-peverify-tool.md).</span><span class="sxs-lookup"><span data-stu-id="68907-216">You should ensure that the transparent code in the assembly is verifiable by using the `transparent` option in the [PEVerify tool](../../../docs/framework/tools/peverify-exe-peverify-tool.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="68907-217">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="68907-217">See also</span></span>

- [<span data-ttu-id="68907-218">Code Transparent de sécurité, niveau 1</span><span class="sxs-lookup"><span data-stu-id="68907-218">Security-Transparent Code, Level 1</span></span>](../../../docs/framework/misc/security-transparent-code-level-1.md)
- [<span data-ttu-id="68907-219">Modifications de sécurité</span><span class="sxs-lookup"><span data-stu-id="68907-219">Security Changes</span></span>](../../../docs/framework/security/security-changes.md)
