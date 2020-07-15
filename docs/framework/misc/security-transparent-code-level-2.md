---
title: Code transparent de sécurité, niveau 2
description: Comprendre le code transparent de niveau 2. Consultez Exemples et comportements d’utilisation, modèles de remplacement, règles d’héritage, et bien plus encore.
ms.date: 03/30/2017
helpviewer_keywords:
- transparency
- level 2 transparency
- security-transparent code
- security-critical code
ms.assetid: 4d05610a-0da6-4f08-acea-d54c9d6143c0
ms.openlocfilehash: 3b87a48ac3f9925fd868be9e58d5904014ca6c09
ms.sourcegitcommit: 0fa2b7b658bf137e813a7f4d09589d64c148ebf5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/14/2020
ms.locfileid: "86309207"
---
# <a name="security-transparent-code-level-2"></a><span data-ttu-id="4c3d0-104">Code transparent de sécurité, niveau 2</span><span class="sxs-lookup"><span data-stu-id="4c3d0-104">Security-Transparent Code, Level 2</span></span>

[!INCLUDE[net_security_note](../../../includes/net-security-note-md.md)]

<span data-ttu-id="4c3d0-105">La transparence de niveau 2 a été introduite dans le .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="4c3d0-105">Level 2 transparency was introduced in the .NET Framework 4.</span></span> <span data-ttu-id="4c3d0-106">Les trois principes de ce modèle sont le code transparent, le code critique sécurisé et le code critique de sécurité.</span><span class="sxs-lookup"><span data-stu-id="4c3d0-106">The three tenets of this model are transparent code, security-safe-critical code, and security-critical code.</span></span>

- <span data-ttu-id="4c3d0-107">Le code transparent, y compris le code qui s'exécute en mode confiance totale, peut appeler d'autre code transparent ou code critique sécurisé uniquement.</span><span class="sxs-lookup"><span data-stu-id="4c3d0-107">Transparent code, including code that is running as full trust, can call other transparent code or security-safe-critical code only.</span></span> <span data-ttu-id="4c3d0-108">Il ne peut effectuer que les actions autorisées par le jeu d'autorisations de confiance partielle du domaine (s'il en existe un).</span><span class="sxs-lookup"><span data-stu-id="4c3d0-108">It can only perform actions allowed by the domain’s partial trust permission set (if one exists).</span></span> <span data-ttu-id="4c3d0-109">Voici ce que le code transparent ne peut pas faire :</span><span class="sxs-lookup"><span data-stu-id="4c3d0-109">Transparent code cannot do the following:</span></span>

  - <span data-ttu-id="4c3d0-110">exécuter un <xref:System.Security.CodeAccessPermission.Assert%2A> ou une élévation de privilège ;</span><span class="sxs-lookup"><span data-stu-id="4c3d0-110">Perform an <xref:System.Security.CodeAccessPermission.Assert%2A> or elevation of privilege.</span></span>

  - <span data-ttu-id="4c3d0-111">contenir du code non sécurisé ou non vérifiable ;</span><span class="sxs-lookup"><span data-stu-id="4c3d0-111">Contain unsafe or unverifiable code.</span></span>

  - <span data-ttu-id="4c3d0-112">appeler directement du code critique ;</span><span class="sxs-lookup"><span data-stu-id="4c3d0-112">Directly call critical code.</span></span>

  - <span data-ttu-id="4c3d0-113">appeler du code natif ou du code possédant l'attribut <xref:System.Security.SuppressUnmanagedCodeSecurityAttribute> ;</span><span class="sxs-lookup"><span data-stu-id="4c3d0-113">Call native code or code with the <xref:System.Security.SuppressUnmanagedCodeSecurityAttribute> attribute.</span></span>

  - <span data-ttu-id="4c3d0-114">appeler un membre protégé par un <xref:System.Security.Permissions.SecurityAction.LinkDemand> ;</span><span class="sxs-lookup"><span data-stu-id="4c3d0-114">Call a member that is protected by a <xref:System.Security.Permissions.SecurityAction.LinkDemand>.</span></span>

  - <span data-ttu-id="4c3d0-115">hériter de types critiques.</span><span class="sxs-lookup"><span data-stu-id="4c3d0-115">Inherit from critical types.</span></span>

  <span data-ttu-id="4c3d0-116">Par ailleurs, les méthodes transparentes ne peuvent pas substituer des méthodes virtuelles critiques ni implémenter des méthodes d'interface critiques.</span><span class="sxs-lookup"><span data-stu-id="4c3d0-116">In addition, transparent methods cannot override critical virtual methods or implement critical interface methods.</span></span>

- <span data-ttu-id="4c3d0-117">Le code critique sécurisé est entièrement fiable, mais peut être appelé par du code transparent.</span><span class="sxs-lookup"><span data-stu-id="4c3d0-117">Safe-critical code is fully trusted but is callable by transparent code.</span></span> <span data-ttu-id="4c3d0-118">Il expose une surface limitée de code de confiance totale ; des vérifications d'exactitude et de sécurité s'opèrent dans le code critique sécurisé.</span><span class="sxs-lookup"><span data-stu-id="4c3d0-118">It exposes a limited surface area of full-trust code; correctness and security verifications happen in safe-critical code.</span></span>

- <span data-ttu-id="4c3d0-119">Le code critique de sécurité peut appeler n'importe quel code et bénéficie d'un niveau de confiance totale, mais il ne peut pas être appelé par du code transparent.</span><span class="sxs-lookup"><span data-stu-id="4c3d0-119">Security-critical code can call any code and is fully trusted, but it cannot be called by transparent code.</span></span>

## <a name="usage-examples-and-behaviors"></a><span data-ttu-id="4c3d0-120">Exemples d'utilisation et comportements</span><span class="sxs-lookup"><span data-stu-id="4c3d0-120">Usage Examples and Behaviors</span></span>

<span data-ttu-id="4c3d0-121">Pour spécifier .NET Framework 4 règles (transparence de niveau 2), utilisez l’annotation suivante pour un assembly :</span><span class="sxs-lookup"><span data-stu-id="4c3d0-121">To specify .NET Framework 4 rules (level 2 transparency), use the following annotation for an assembly:</span></span>

```csharp
[assembly: SecurityRules(SecurityRuleSet.Level2)]
```

<span data-ttu-id="4c3d0-122">Pour verrouiller les règles du .NET Framework 2.0 (transparence de niveau 1), utilisez l'annotation suivante :</span><span class="sxs-lookup"><span data-stu-id="4c3d0-122">To lock into the .NET Framework 2.0 rules (level 1 transparency), use the following annotation:</span></span>

```csharp
[assembly: SecurityRules(SecurityRuleSet.Level1)]
```

<span data-ttu-id="4c3d0-123">Si vous n’annotez pas un assembly, les règles .NET Framework 4 sont utilisées par défaut.</span><span class="sxs-lookup"><span data-stu-id="4c3d0-123">If you do not annotate an assembly, the .NET Framework 4 rules are used by default.</span></span> <span data-ttu-id="4c3d0-124">Toutefois, la meilleure pratique recommandée consiste à utiliser l' <xref:System.Security.SecurityRulesAttribute> attribut au lieu de dépendre de la valeur par défaut.</span><span class="sxs-lookup"><span data-stu-id="4c3d0-124">However, the recommended best practice is to use the <xref:System.Security.SecurityRulesAttribute> attribute instead of depending on the default.</span></span>

### <a name="assembly-wide-annotation"></a><span data-ttu-id="4c3d0-125">Annotation à l'échelle de l'assembly</span><span class="sxs-lookup"><span data-stu-id="4c3d0-125">Assembly-wide Annotation</span></span>

<span data-ttu-id="4c3d0-126">Les règles suivantes s'appliquent à l'utilisation d'attributs au niveau de l'assembly :</span><span class="sxs-lookup"><span data-stu-id="4c3d0-126">The following rules apply to the use of attributes at the assembly level:</span></span>

- <span data-ttu-id="4c3d0-127">Aucun attribut : si vous ne spécifiez aucun attribut, le runtime considère l'ensemble du code comme du code critique de sécurité, sauf si le fait d'être critique de sécurité va à l'encontre d'une règle d'héritage (par exemple, en cas de substitution ou d'implémentation d'une méthode d'interface ou virtuelle transparente).</span><span class="sxs-lookup"><span data-stu-id="4c3d0-127">No attributes: If you do not specify any attributes, the runtime interprets all code as security-critical, except where being security-critical violates an inheritance rule (for example, when overriding or implementing a transparent virtual or interface method).</span></span> <span data-ttu-id="4c3d0-128">Dans ces cas de figure, les méthodes sont critiques sécurisées.</span><span class="sxs-lookup"><span data-stu-id="4c3d0-128">In those cases, the methods are safe-critical.</span></span> <span data-ttu-id="4c3d0-129">Si vous ne spécifiez aucun attribut, le common language runtime détermine les règles de transparence à votre place.</span><span class="sxs-lookup"><span data-stu-id="4c3d0-129">Specifying no attribute causes the common language runtime to determine the transparency rules for you.</span></span>

- <span data-ttu-id="4c3d0-130">`SecurityTransparent` : tout le code est transparent ; l'assembly dans son ensemble ne fait rien de privilégié ou de non sécurisé.</span><span class="sxs-lookup"><span data-stu-id="4c3d0-130">`SecurityTransparent`: All code is transparent; the entire assembly will not do anything privileged or unsafe.</span></span>

- <span data-ttu-id="4c3d0-131">`SecurityCritical` : tout le code introduit par des types dans cet assembly est critique ; le reste du code est transparent.</span><span class="sxs-lookup"><span data-stu-id="4c3d0-131">`SecurityCritical`: All code that is introduced by types in this assembly is critical; all other code is transparent.</span></span> <span data-ttu-id="4c3d0-132">Ce scénario équivaut à ne spécifier aucun attribut ; cependant, le common language runtime ne détermine pas automatiquement les règles de transparence.</span><span class="sxs-lookup"><span data-stu-id="4c3d0-132">This scenario is similar to not specifying any attributes; however, the common language runtime does not automatically determine the transparency rules.</span></span> <span data-ttu-id="4c3d0-133">Par exemple, si vous substituez une méthode virtuelle ou abstraite ou que vous implémentez une méthode d'interface, par défaut, cette méthode est transparente.</span><span class="sxs-lookup"><span data-stu-id="4c3d0-133">For example, if you override a virtual or abstract method or implement an interface method, by default, that method is transparent.</span></span> <span data-ttu-id="4c3d0-134">Vous devez annoter explicitement la méthode comme étant `SecurityCritical` ou `SecuritySafeCritical` ; sinon, une exception <xref:System.TypeLoadException> est levée au moment du chargement.</span><span class="sxs-lookup"><span data-stu-id="4c3d0-134">You must explicitly annotate the method as `SecurityCritical` or `SecuritySafeCritical`; otherwise, a <xref:System.TypeLoadException> will be thrown at load time.</span></span> <span data-ttu-id="4c3d0-135">Cette règle vaut aussi quand la classe de base et la classe dérivée se trouvent dans le même assembly.</span><span class="sxs-lookup"><span data-stu-id="4c3d0-135">This rule also applies when both the base class and the derived class are in the same assembly.</span></span>

- <span data-ttu-id="4c3d0-136">`AllowPartiallyTrustedCallers` (niveau 2 uniquement) : tout le code est transparent par défaut.</span><span class="sxs-lookup"><span data-stu-id="4c3d0-136">`AllowPartiallyTrustedCallers` (level 2 only): All code defaults to transparent.</span></span> <span data-ttu-id="4c3d0-137">Cependant, chaque type et membre individuel peut avoir d'autres attributs.</span><span class="sxs-lookup"><span data-stu-id="4c3d0-137">However, individual types and members can have other attributes.</span></span>

<span data-ttu-id="4c3d0-138">Le tableau suivant compare le comportement au niveau de l’assembly pour le niveau 2 avec le niveau 1.</span><span class="sxs-lookup"><span data-stu-id="4c3d0-138">The following table compares the assembly level behavior for Level 2 with Level 1.</span></span>

|<span data-ttu-id="4c3d0-139">Attribut d’assembly</span><span class="sxs-lookup"><span data-stu-id="4c3d0-139">Assembly attribute</span></span>|<span data-ttu-id="4c3d0-140">Niveau 2</span><span class="sxs-lookup"><span data-stu-id="4c3d0-140">Level 2</span></span>|<span data-ttu-id="4c3d0-141">Niveau 1</span><span class="sxs-lookup"><span data-stu-id="4c3d0-141">Level 1</span></span>|
|------------------------|-------------|-------------|
|<span data-ttu-id="4c3d0-142">Aucun attribut sur un assembly de niveau de confiance partielle</span><span class="sxs-lookup"><span data-stu-id="4c3d0-142">No attribute on a partially trusted assembly</span></span>|<span data-ttu-id="4c3d0-143">Les types et les membres sont transparents par défaut, mais peuvent être critiques de sécurité ou critiques sécurisés.</span><span class="sxs-lookup"><span data-stu-id="4c3d0-143">Types and members are by default transparent, but can be security-critical or security-safe-critical.</span></span>|<span data-ttu-id="4c3d0-144">Tous les types et membres sont transparents.</span><span class="sxs-lookup"><span data-stu-id="4c3d0-144">All types and members are transparent.</span></span>|
|<span data-ttu-id="4c3d0-145">Aucun attribut</span><span class="sxs-lookup"><span data-stu-id="4c3d0-145">No attribute</span></span>|<span data-ttu-id="4c3d0-146">Si vous ne spécifiez aucun attribut, le common language runtime détermine les règles de transparence à votre place.</span><span class="sxs-lookup"><span data-stu-id="4c3d0-146">Specifying no attribute causes the common language runtime to determine the transparency rules for you.</span></span> <span data-ttu-id="4c3d0-147">Tous les types et membres sont critiques de sécurité, sauf si le fait d'être critique de sécurité va à l'encontre d'une règle d'héritage.</span><span class="sxs-lookup"><span data-stu-id="4c3d0-147">All types and members are security-critical, except where being security-critical violates an inheritance rule.</span></span>|<span data-ttu-id="4c3d0-148">Sur un assembly d'un niveau de confiance totale (dans le Global Assembly Cache ou s'il est identifié comme étant entièrement fiable dans le `AppDomain`) tous les types sont transparents et tous les membres sont critiques sécurisés.</span><span class="sxs-lookup"><span data-stu-id="4c3d0-148">On a fully trusted assembly (in the global assembly cache or identified as full trust in the `AppDomain`) all types are transparent and all members are security-safe-critical.</span></span>|
|`SecurityTransparent`|<span data-ttu-id="4c3d0-149">Tous les types et membres sont transparents.</span><span class="sxs-lookup"><span data-stu-id="4c3d0-149">All types and members are transparent.</span></span>|<span data-ttu-id="4c3d0-150">Tous les types et membres sont transparents.</span><span class="sxs-lookup"><span data-stu-id="4c3d0-150">All types and members are transparent.</span></span>|
|`SecurityCritical(SecurityCriticalScope.Everything)`|<span data-ttu-id="4c3d0-151">Non applicable.</span><span class="sxs-lookup"><span data-stu-id="4c3d0-151">Not applicable.</span></span>|<span data-ttu-id="4c3d0-152">Tous les types et membres sont critiques de sécurité.</span><span class="sxs-lookup"><span data-stu-id="4c3d0-152">All types and members are security-critical.</span></span>|
|`SecurityCritical`|<span data-ttu-id="4c3d0-153">Tout le code introduit par des types dans cet assembly est critique ; le reste du code est transparent.</span><span class="sxs-lookup"><span data-stu-id="4c3d0-153">All code that is introduced by types in this assembly is critical; all other code is transparent.</span></span> <span data-ttu-id="4c3d0-154">Si vous substituez une méthode virtuelle ou abstraite ou que vous implémentez une méthode d'interface, vous devez annoter explicitement la méthode comme étant `SecurityCritical` ou `SecuritySafeCritical`.</span><span class="sxs-lookup"><span data-stu-id="4c3d0-154">If you override a virtual or abstract method or implement an interface method, you must explicitly annotate the method as `SecurityCritical` or `SecuritySafeCritical`.</span></span>|<span data-ttu-id="4c3d0-155">Tout le code est transparent par défaut.</span><span class="sxs-lookup"><span data-stu-id="4c3d0-155">All code defaults to transparent.</span></span> <span data-ttu-id="4c3d0-156">Cependant, chaque type et membre individuel peut avoir d'autres attributs.</span><span class="sxs-lookup"><span data-stu-id="4c3d0-156">However, individual types and members can have other attributes.</span></span>|

### <a name="type-and-member-annotation"></a><span data-ttu-id="4c3d0-157">Annotation de type et de membre</span><span class="sxs-lookup"><span data-stu-id="4c3d0-157">Type and Member Annotation</span></span>

<span data-ttu-id="4c3d0-158">Les attributs de sécurité qui s'appliquent à un type s'appliquent aussi aux membres introduits par ce type.</span><span class="sxs-lookup"><span data-stu-id="4c3d0-158">The security attributes that are applied to a type also apply to the members that are introduced by the type.</span></span> <span data-ttu-id="4c3d0-159">En revanche, ils ne s'appliquent pas aux substitutions virtuelles ou abstraites des implémentations de classe ou d'interface de base.</span><span class="sxs-lookup"><span data-stu-id="4c3d0-159">However, they do not apply to virtual or abstract overrides of the base class or interface implementations.</span></span> <span data-ttu-id="4c3d0-160">L'utilisation d'attributs au niveau du type et du membre obéit aux règles suivantes :</span><span class="sxs-lookup"><span data-stu-id="4c3d0-160">The following rules apply to the use of attributes at the type and member level:</span></span>

- <span data-ttu-id="4c3d0-161">`SecurityCritical` : le type ou le membre est critique et peut être appelé uniquement par du code de niveau de confiance totale.</span><span class="sxs-lookup"><span data-stu-id="4c3d0-161">`SecurityCritical`: The type or member is critical and can be called only by full-trust code.</span></span> <span data-ttu-id="4c3d0-162">Les méthodes introduites dans un type critique de sécurité sont critiques.</span><span class="sxs-lookup"><span data-stu-id="4c3d0-162">Methods that are introduced in a security-critical type are critical.</span></span>

    > [!IMPORTANT]
    > <span data-ttu-id="4c3d0-163">Les méthodes virtuelles et abstraites introduites dans des classes ou interfaces de base et substituées ou implémentées dans une classe critique de sécurité sont transparentes par défaut.</span><span class="sxs-lookup"><span data-stu-id="4c3d0-163">Virtual and abstract methods that are introduced in base classes or interfaces, and overridden or implemented in a security-critical class are transparent by default.</span></span> <span data-ttu-id="4c3d0-164">Elles doivent être identifiées comme étant `SecuritySafeCritical` ou `SecurityCritical`.</span><span class="sxs-lookup"><span data-stu-id="4c3d0-164">They must be identified as either `SecuritySafeCritical` or `SecurityCritical`.</span></span>

- <span data-ttu-id="4c3d0-165">`SecuritySafeCritical` : le type ou le membre est critique sécurisé.</span><span class="sxs-lookup"><span data-stu-id="4c3d0-165">`SecuritySafeCritical`: The type or member is safe-critical.</span></span> <span data-ttu-id="4c3d0-166">Cependant, le type ou le membre peut être appelé à partir d'un code transparent (de niveau de confiance partielle) et a les mêmes capacités que n'importe quel autre code critique.</span><span class="sxs-lookup"><span data-stu-id="4c3d0-166">However, the type or member can be called from transparent (partially trusted) code and is as capable as any other critical code.</span></span> <span data-ttu-id="4c3d0-167">La sécurité du code doit faire l'objet d'un audit.</span><span class="sxs-lookup"><span data-stu-id="4c3d0-167">The code must be audited for security.</span></span>

## <a name="override-patterns"></a><span data-ttu-id="4c3d0-168">Modèles de substitution</span><span class="sxs-lookup"><span data-stu-id="4c3d0-168">Override Patterns</span></span>

<span data-ttu-id="4c3d0-169">Le tableau suivant présente les substitutions de méthodes autorisées pour la transparence de niveau 2.</span><span class="sxs-lookup"><span data-stu-id="4c3d0-169">The following table shows the method overrides allowed for level 2 transparency.</span></span>

|<span data-ttu-id="4c3d0-170">Membre d'interface/virtuel de base</span><span class="sxs-lookup"><span data-stu-id="4c3d0-170">Base virtual/interface member</span></span>|<span data-ttu-id="4c3d0-171">Substitution/interface</span><span class="sxs-lookup"><span data-stu-id="4c3d0-171">Override/interface</span></span>|
|------------------------------------|-------------------------|
|`Transparent`|`Transparent`|
|`Transparent`|`SafeCritical`|
|`SafeCritical`|`Transparent`|
|`SafeCritical`|`SafeCritical`|
|`Critical`|`Critical`|

## <a name="inheritance-rules"></a><span data-ttu-id="4c3d0-172">Règles d'héritage</span><span class="sxs-lookup"><span data-stu-id="4c3d0-172">Inheritance Rules</span></span>

<span data-ttu-id="4c3d0-173">Dans cette section, l'ordre suivant est attribué au code `Transparent`, `Critical` et `SafeCritical` en fonction de l'accès et des fonctionnalités :</span><span class="sxs-lookup"><span data-stu-id="4c3d0-173">In this section, the following order is assigned to `Transparent`, `Critical`, and `SafeCritical` code based on access and capabilities:</span></span>

`Transparent` < `SafeCritical` < `Critical`

- <span data-ttu-id="4c3d0-174">Règles pour les types : allant de gauche à droite, l'accès devient plus restrictif.</span><span class="sxs-lookup"><span data-stu-id="4c3d0-174">Rules for types: Going from left to right, access becomes more restrictive.</span></span> <span data-ttu-id="4c3d0-175">Les types dérivés doivent être au moins aussi restrictifs que le type de base.</span><span class="sxs-lookup"><span data-stu-id="4c3d0-175">Derived types must be at least as restrictive as the base type.</span></span>

- <span data-ttu-id="4c3d0-176">Règles pour les méthodes : les méthodes dérivées ne peuvent pas modifier l'accessibilité à partir de la méthode de base.</span><span class="sxs-lookup"><span data-stu-id="4c3d0-176">Rules for methods: Derived methods cannot change accessibility from the base method.</span></span> <span data-ttu-id="4c3d0-177">Pour le comportement par défaut, toutes les méthodes dérivées qui ne sont pas annotées sont `Transparent`.</span><span class="sxs-lookup"><span data-stu-id="4c3d0-177">For default behavior, all derived methods that are not annotated are `Transparent`.</span></span> <span data-ttu-id="4c3d0-178">Les dérivés des types critiques provoquent une exception si la méthode substituée n’est pas explicitement annotée comme étant `SecurityCritical`.</span><span class="sxs-lookup"><span data-stu-id="4c3d0-178">Derivatives of critical types cause an exception to be thrown if the overridden method is not explicitly annotated as `SecurityCritical`.</span></span>

<span data-ttu-id="4c3d0-179">Le tableau suivant présente les modèles d'héritage de type autorisés.</span><span class="sxs-lookup"><span data-stu-id="4c3d0-179">The following table shows the allowed type inheritance patterns.</span></span>

|<span data-ttu-id="4c3d0-180">Classe de base</span><span class="sxs-lookup"><span data-stu-id="4c3d0-180">Base class</span></span>|<span data-ttu-id="4c3d0-181">La classe dérivée peut être</span><span class="sxs-lookup"><span data-stu-id="4c3d0-181">Derived class can be</span></span>|
|----------------|--------------------------|
|`Transparent`|`Transparent`|
|`Transparent`|`SafeCritical`|
|`Transparent`|`Critical`|
|`SafeCritical`|`SafeCritical`|
|`SafeCritical`|`Critical`|
|`Critical`|`Critical`|

<span data-ttu-id="4c3d0-182">Le tableau suivant présente les modèles d’héritage de type non autorisés.</span><span class="sxs-lookup"><span data-stu-id="4c3d0-182">The following table shows the disallowed type inheritance patterns.</span></span>

|<span data-ttu-id="4c3d0-183">Classe de base</span><span class="sxs-lookup"><span data-stu-id="4c3d0-183">Base class</span></span>|<span data-ttu-id="4c3d0-184">La classe dérivée ne peut pas être</span><span class="sxs-lookup"><span data-stu-id="4c3d0-184">Derived class cannot be</span></span>|
|----------------|-----------------------------|
|`SafeCritical`|`Transparent`|
|`Critical`|`Transparent`|
|`Critical`|`SafeCritical`|

<span data-ttu-id="4c3d0-185">Le tableau suivant présente les modèles d'héritage de méthode autorisés.</span><span class="sxs-lookup"><span data-stu-id="4c3d0-185">The following table shows the allowed method inheritance patterns.</span></span>

|<span data-ttu-id="4c3d0-186">Méthode de base</span><span class="sxs-lookup"><span data-stu-id="4c3d0-186">Base method</span></span>|<span data-ttu-id="4c3d0-187">La méthode dérivée peut être</span><span class="sxs-lookup"><span data-stu-id="4c3d0-187">Derived method can be</span></span>|
|-----------------|---------------------------|
|`Transparent`|`Transparent`|
|`Transparent`|`SafeCritical`|
|`SafeCritical`|`Transparent`|
|`SafeCritical`|`SafeCritical`|
|`Critical`|`Critical`|

<span data-ttu-id="4c3d0-188">Le tableau suivant présente les modèles d'héritage de méthode non autorisés.</span><span class="sxs-lookup"><span data-stu-id="4c3d0-188">The following table shows the disallowed method inheritance patterns.</span></span>

|<span data-ttu-id="4c3d0-189">Méthode de base</span><span class="sxs-lookup"><span data-stu-id="4c3d0-189">Base method</span></span>|<span data-ttu-id="4c3d0-190">La méthode dérivée ne peut pas être</span><span class="sxs-lookup"><span data-stu-id="4c3d0-190">Derived method cannot be</span></span>|
|-----------------|------------------------------|
|`Transparent`|`Critical`|
|`SafeCritical`|`Critical`|
|`Critical`|`Transparent`|
|`Critical`|`SafeCritical`|

> [!NOTE]
> <span data-ttu-id="4c3d0-191">Ces règles d'héritage s'appliquent aux types et membres de niveau 2.</span><span class="sxs-lookup"><span data-stu-id="4c3d0-191">These inheritance rules apply to level 2 types and members.</span></span> <span data-ttu-id="4c3d0-192">Les types contenus dans les assemblys de niveau 1 peuvent hériter des types et membres critiques de sécurité de niveau 2.</span><span class="sxs-lookup"><span data-stu-id="4c3d0-192">Types in level 1 assemblies can inherit from level 2 security-critical types and members.</span></span> <span data-ttu-id="4c3d0-193">Par conséquent, les types et membres de niveau 2 doivent avoir des demandes d'héritage distinctes pour les héritiers de niveau 1.</span><span class="sxs-lookup"><span data-stu-id="4c3d0-193">Therefore, level 2 types and members must have separate inheritance demands for level 1 inheritors.</span></span>

## <a name="additional-information-and-rules"></a><span data-ttu-id="4c3d0-194">Informations et règles supplémentaires</span><span class="sxs-lookup"><span data-stu-id="4c3d0-194">Additional Information and Rules</span></span>

### <a name="linkdemand-support"></a><span data-ttu-id="4c3d0-195">Prise en charge de LinkDemand</span><span class="sxs-lookup"><span data-stu-id="4c3d0-195">LinkDemand Support</span></span>

<span data-ttu-id="4c3d0-196">Le modèle de transparence de niveau 2 remplace le <xref:System.Security.Permissions.SecurityAction.LinkDemand> par l'attribut <xref:System.Security.SecurityCriticalAttribute>.</span><span class="sxs-lookup"><span data-stu-id="4c3d0-196">The level 2 transparency model replaces the <xref:System.Security.Permissions.SecurityAction.LinkDemand> with the <xref:System.Security.SecurityCriticalAttribute> attribute.</span></span> <span data-ttu-id="4c3d0-197">Dans le code hérité (de niveau 1), un <xref:System.Security.Permissions.SecurityAction.LinkDemand> est automatiquement traité comme un <xref:System.Security.Permissions.SecurityAction.Demand>.</span><span class="sxs-lookup"><span data-stu-id="4c3d0-197">In legacy (level 1) code, a <xref:System.Security.Permissions.SecurityAction.LinkDemand> is automatically treated as a <xref:System.Security.Permissions.SecurityAction.Demand>.</span></span>

### <a name="reflection"></a><span data-ttu-id="4c3d0-198">Réflexion</span><span class="sxs-lookup"><span data-stu-id="4c3d0-198">Reflection</span></span>

<span data-ttu-id="4c3d0-199">L'appel d'une méthode critique ou la lecture d'un champ critique déclenche une demande de confiance totale (comme si vous appeliez une méthode ou un champ privé).</span><span class="sxs-lookup"><span data-stu-id="4c3d0-199">Invoking a critical method or reading a critical field triggers a demand for full trust (just as if you were invoking a private method or field).</span></span> <span data-ttu-id="4c3d0-200">Autrement dit, du code de niveau de confiance totale peut appeler une méthode critique, alors que du code de niveau de confiance partielle ne le peut pas.</span><span class="sxs-lookup"><span data-stu-id="4c3d0-200">Therefore, full-trust code can invoke a critical method, whereas partial-trust code cannot.</span></span>

<span data-ttu-id="4c3d0-201">Les propriétés suivantes ont été ajoutées à l'espace de noms <xref:System.Reflection> pour déterminer si le type, la méthode ou le champ est `SecurityCritical`, `SecuritySafeCritical` ou `SecurityTransparent` : <xref:System.Type.IsSecurityCritical%2A>, <xref:System.Reflection.MethodBase.IsSecuritySafeCritical%2A> et <xref:System.Reflection.MethodBase.IsSecurityTransparent%2A>.</span><span class="sxs-lookup"><span data-stu-id="4c3d0-201">The following properties have been added to the <xref:System.Reflection> namespace to determine whether the type, method, or field is `SecurityCritical`, `SecuritySafeCritical`, or `SecurityTransparent`:  <xref:System.Type.IsSecurityCritical%2A>, <xref:System.Reflection.MethodBase.IsSecuritySafeCritical%2A>, and <xref:System.Reflection.MethodBase.IsSecurityTransparent%2A>.</span></span> <span data-ttu-id="4c3d0-202">Ces propriétés permettent de déterminer la transparence par la réflexion plutôt que par la vérification de la présence de l'attribut.</span><span class="sxs-lookup"><span data-stu-id="4c3d0-202">Use these properties to determine transparency by using reflection instead of checking for the presence of the attribute.</span></span> <span data-ttu-id="4c3d0-203">Compte tenu de la complexité des règles de transparence, vérifier la présence de l'attribut peut ne pas suffire.</span><span class="sxs-lookup"><span data-stu-id="4c3d0-203">The transparency rules are complex, and checking for the attribute may not be sufficient.</span></span>

> [!NOTE]
> <span data-ttu-id="4c3d0-204">Une `SafeCritical` méthode retourne `true` pour <xref:System.Type.IsSecurityCritical%2A> et <xref:System.Reflection.MethodBase.IsSecuritySafeCritical%2A> , car `SafeCritical` est effectivement critique (elle a les mêmes fonctionnalités que le code critique, mais elle peut être appelée à partir du code transparent).</span><span class="sxs-lookup"><span data-stu-id="4c3d0-204">A `SafeCritical` method returns `true` for both <xref:System.Type.IsSecurityCritical%2A> and <xref:System.Reflection.MethodBase.IsSecuritySafeCritical%2A>, because `SafeCritical` is indeed critical (it has the same capabilities as critical code, but it can be called from transparent code).</span></span>

<span data-ttu-id="4c3d0-205">Les méthodes dynamiques héritent de la transparence des modules auxquels elles sont attachées ; elles n'héritent pas de la transparence du type (si elles sont attachées à un type).</span><span class="sxs-lookup"><span data-stu-id="4c3d0-205">Dynamic methods inherit the transparency of the modules they are attached to; they do not inherit the transparency of the type (if they are attached to a type).</span></span>

### <a name="skip-verification-in-full-trust"></a><span data-ttu-id="4c3d0-206">Ignorer la vérification en mode confiance totale</span><span class="sxs-lookup"><span data-stu-id="4c3d0-206">Skip Verification in Full Trust</span></span>

<span data-ttu-id="4c3d0-207">Vous pouvez ignorer la vérification pour les assemblys transparents de niveau de confiance totale en attribuant à la propriété <xref:System.Security.SecurityRulesAttribute.SkipVerificationInFullTrust%2A> la valeur `true` dans l'attribut <xref:System.Security.SecurityRulesAttribute> :</span><span class="sxs-lookup"><span data-stu-id="4c3d0-207">You can skip verification for fully trusted transparent assemblies by setting the <xref:System.Security.SecurityRulesAttribute.SkipVerificationInFullTrust%2A> property to `true` in the <xref:System.Security.SecurityRulesAttribute> attribute:</span></span>

`[assembly: SecurityRules(SecurityRuleSet.Level2, SkipVerificationInFullTrust = true)]`

<span data-ttu-id="4c3d0-208">La valeur par défaut de la propriété <xref:System.Security.SecurityRulesAttribute.SkipVerificationInFullTrust%2A> étant `false`, elle doit avoir la valeur `true` pour ignorer la vérification.</span><span class="sxs-lookup"><span data-stu-id="4c3d0-208">The <xref:System.Security.SecurityRulesAttribute.SkipVerificationInFullTrust%2A> property is `false` by default, so the property must be set to `true` to skip verification.</span></span> <span data-ttu-id="4c3d0-209">Cela doit être fait uniquement à des fins d'optimisation.</span><span class="sxs-lookup"><span data-stu-id="4c3d0-209">This should be done for optimization purposes only.</span></span> <span data-ttu-id="4c3d0-210">Vous devez vous assurer que le code transparent de l’assembly peut être vérifié à l’aide `transparent` de l’option dans l' [outil PEVerify](../tools/peverify-exe-peverify-tool.md).</span><span class="sxs-lookup"><span data-stu-id="4c3d0-210">You should ensure that the transparent code in the assembly is verifiable by using the `transparent` option in the [PEVerify tool](../tools/peverify-exe-peverify-tool.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="4c3d0-211">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="4c3d0-211">See also</span></span>

- [<span data-ttu-id="4c3d0-212">Code transparent de sécurité, niveau 1</span><span class="sxs-lookup"><span data-stu-id="4c3d0-212">Security-Transparent Code, Level 1</span></span>](security-transparent-code-level-1.md)
- [<span data-ttu-id="4c3d0-213">Modifications de sécurité</span><span class="sxs-lookup"><span data-stu-id="4c3d0-213">Security Changes</span></span>](https://docs.microsoft.com/previous-versions/dotnet/framework/security/security-changes)
