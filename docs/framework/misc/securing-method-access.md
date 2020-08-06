---
title: Sécurisation de l'accès à la méthode
description: Apprenez à sécuriser l’accès à la méthode pour les méthodes qui ne sont pas destinées à une utilisation publique, mais qui doivent tout de même être publiques.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- code security, method access
- secure coding, method access
- security [.NET Framework], method access
- method access security
ms.assetid: f7c2d6ec-3b18-4e0e-9991-acd97189d818
ms.openlocfilehash: 88868ab29fc37854959a044b9c0fed5bd8c82d77
ms.sourcegitcommit: c37e8d4642fef647ebab0e1c618ecc29ddfe2a0f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/06/2020
ms.locfileid: "87855762"
---
# <a name="securing-method-access"></a><span data-ttu-id="06808-103">Sécurisation de l'accès à la méthode</span><span class="sxs-lookup"><span data-stu-id="06808-103">Securing Method Access</span></span>

[!INCLUDE[net_security_note](../../../includes/net-security-note-md.md)]  
  
 <span data-ttu-id="06808-104">Il est possible que certaines méthodes ne conviennent pas à l'appel par du code arbitraire non fiable.</span><span class="sxs-lookup"><span data-stu-id="06808-104">Some methods might not be suitable to allow arbitrary untrusted code to call.</span></span> <span data-ttu-id="06808-105">Ces méthodes présentent plusieurs risques : la méthode peut fournir des informations restreintes ; elle peut croire aux informations qui lui sont passées ; elle peut ne pas faire de vérification d'erreurs sur les paramètres ; ou dans le cas de paramètres erronés, la méthode peut dysfonctionner ou avoir des effets préjudiciables.</span><span class="sxs-lookup"><span data-stu-id="06808-105">Such methods pose several risks: The method might provide some restricted information; it might believe any information passed to it; it might not do error checking on the parameters; or with the wrong parameters, it might malfunction or do something harmful.</span></span> <span data-ttu-id="06808-106">Vous devez connaître ces cas et adopter la bonne marche à suivre pour sécuriser la méthode.</span><span class="sxs-lookup"><span data-stu-id="06808-106">You should be aware of these cases and take action to help protect the method.</span></span>  
  
 <span data-ttu-id="06808-107">Dans certains cas, vous devrez peut-être limiter les méthodes qui ne sont pas destinées à une utilisation publique, mais qui doivent cependant être publiques.</span><span class="sxs-lookup"><span data-stu-id="06808-107">In some cases, you might need to restrict methods that are not intended for public use but still must be public.</span></span> <span data-ttu-id="06808-108">Par exemple, dans le cas d'une interface qui doit être appelée sur vos DLL, et donc être publique, celle-ci ne doit pas toutefois être exposée de manière publique afin d'empêcher son utilisation par des clients ou d'empêcher l'exploitation par du code nuisible du point d'entrée dans votre composant.</span><span class="sxs-lookup"><span data-stu-id="06808-108">For example, you might have an interface that needs to be called across your own DLLs and hence must be public, but you do not want to expose it publicly to prevent customers from using it or to prevent malicious code from exploiting the entry point into your component.</span></span> <span data-ttu-id="06808-109">Une autre raison courante de restreindre une méthode non destinée à une utilisation publique (mais qui doit être publique) consiste à éviter d’avoir à documenter et à prendre en charge ce qui peut être une interface interne.</span><span class="sxs-lookup"><span data-stu-id="06808-109">Another common reason to restrict a method not intended for public use (but that must be public) is to avoid having to document and support what might be an internal interface.</span></span>  
  
 <span data-ttu-id="06808-110">Le code managé propose plusieurs façons de limiter l'accès à la méthode :</span><span class="sxs-lookup"><span data-stu-id="06808-110">Managed code offers several ways to restrict method access:</span></span>  
  
- <span data-ttu-id="06808-111">Limitez l'étendue de l'accessibilité à la classe, à l'assembly ou aux classes dérivées, s'ils sont de confiance.</span><span class="sxs-lookup"><span data-stu-id="06808-111">Limit the scope of accessibility to the class, assembly, or derived classes, if they can be trusted.</span></span> <span data-ttu-id="06808-112">C'est la façon la plus simple de limiter l'accès à la méthode.</span><span class="sxs-lookup"><span data-stu-id="06808-112">This is the simplest way to limit method access.</span></span> <span data-ttu-id="06808-113">En général, les classes dérivées peuvent être moins dignes de confiance que la classe à partir de laquelle elles dérivent, mais dans certains cas, elles partagent l’identité de la classe parente.</span><span class="sxs-lookup"><span data-stu-id="06808-113">In general, derived classes can be less trustworthy than the class they derive from, though in some cases they share the parent class's identity.</span></span> <span data-ttu-id="06808-114">En particulier, ne déduisez pas l’approbation à partir du mot clé `protected` , qui n’est pas nécessairement utilisé dans le contexte de sécurité.</span><span class="sxs-lookup"><span data-stu-id="06808-114">In particular, do not infer trust from the keyword `protected`, which is not necessarily used in the security context.</span></span>  
  
- <span data-ttu-id="06808-115">Limitez l’accès à la méthode aux appelants d’une identité spécifiée (essentiellement, toute [preuve](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/7y5x1hcd%28v=vs.100%29) particulière (nom fort, éditeur, zone, etc.) que vous choisissez.</span><span class="sxs-lookup"><span data-stu-id="06808-115">Limit the method access to callers of a specified identity--essentially, any particular [evidence](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/7y5x1hcd%28v=vs.100%29) (strong name, publisher, zone, and so on) you choose.</span></span>  
  
- <span data-ttu-id="06808-116">Limitez l'accès à la méthode aux appelants dont les autorisations correspondent à celles que vous choisissez.</span><span class="sxs-lookup"><span data-stu-id="06808-116">Limit the method access to callers having whatever permissions you select.</span></span>  
  
 <span data-ttu-id="06808-117">De même, la sécurité déclarative vous permet de contrôler l'héritage de classes.</span><span class="sxs-lookup"><span data-stu-id="06808-117">Similarly, declarative security allows you to control inheritance of classes.</span></span> <span data-ttu-id="06808-118">Vous pouvez utiliser **InheritanceDemand** pour effectuer les opérations suivantes :</span><span class="sxs-lookup"><span data-stu-id="06808-118">You can use **InheritanceDemand** to do the following:</span></span>  
  
- <span data-ttu-id="06808-119">Obliger des classes dérivées à posséder une identité ou une autorisation spécifiée.</span><span class="sxs-lookup"><span data-stu-id="06808-119">Require derived classes to have a specified identity or permission.</span></span>  
  
- <span data-ttu-id="06808-120">Obliger des classes dérivées qui substituent des méthodes spécifiques à posséder une identité ou une autorisation spécifiée.</span><span class="sxs-lookup"><span data-stu-id="06808-120">Require derived classes that override specific methods to have a specified identity or permission.</span></span>  
  
 <span data-ttu-id="06808-121">L'exemple suivant montre comment sécuriser une classe public pour un accès limité en imposant que les appelants soient signés avec un nom fort particulier.</span><span class="sxs-lookup"><span data-stu-id="06808-121">The following example shows how to help protect a public class for limited access by requiring that callers be signed with a particular strong name.</span></span> <span data-ttu-id="06808-122">Cet exemple utilise le <xref:System.Security.Permissions.StrongNameIdentityPermissionAttribute> avec une **demande** pour le nom fort.</span><span class="sxs-lookup"><span data-stu-id="06808-122">This example uses the <xref:System.Security.Permissions.StrongNameIdentityPermissionAttribute> with a **Demand** for the strong name.</span></span> <span data-ttu-id="06808-123">Pour obtenir des informations sur les tâches relatives à la signature d’un assembly avec un nom fort, consultez [création et utilisation d’assemblys](../../standard/assembly/create-use-strong-named.md)avec nom fort.</span><span class="sxs-lookup"><span data-stu-id="06808-123">For task-based information on how to sign an assembly with a strong name, see [Creating and Using Strong-Named Assemblies](../../standard/assembly/create-use-strong-named.md).</span></span>  
  
```vb  
<StrongNameIdentityPermissionAttribute(SecurityAction.Demand, PublicKey := "…hex…", Name := "App1", Version := "0.0.0.0")>  _  
Public Class Class1  
End Class  
```  
  
```csharp  
[StrongNameIdentityPermissionAttribute(SecurityAction.Demand, PublicKey="…hex…", Name="App1", Version="0.0.0.0")]  
public class Class1  
{  
  
}
```  
  
## <a name="excluding-classes-and-members-from-use-by-untrusted-code"></a><span data-ttu-id="06808-124">Exclusion des classes et des membres d'une utilisation par du code non fiable</span><span class="sxs-lookup"><span data-stu-id="06808-124">Excluding Classes and Members from Use by Untrusted Code</span></span>  
 <span data-ttu-id="06808-125">Utilisez les déclarations illustrées dans cette section pour empêcher des classes et des méthodes spécifiques, ainsi que des propriétés et des événements, d'être utilisés par du code d'un niveau de confiance partiel.</span><span class="sxs-lookup"><span data-stu-id="06808-125">Use the declarations shown in this section to prevent specific classes and methods, as well as properties and events, from being used by partially trusted code.</span></span> <span data-ttu-id="06808-126">En appliquant ces déclarations à une classe, vous appliquez la protection à toutes ses méthodes, propriétés et événements.</span><span class="sxs-lookup"><span data-stu-id="06808-126">By applying these declarations to a class, you apply the protection to all its methods, properties, and events.</span></span> <span data-ttu-id="06808-127">Toutefois, l’accès au champ n’est pas affecté par la sécurité déclarative.</span><span class="sxs-lookup"><span data-stu-id="06808-127">However, field access is not affected by declarative security.</span></span> <span data-ttu-id="06808-128">Notez également que les demandes de liaison ne protègent que contre les appelants immédiats et peuvent toujours faire l'objet d'attaques malveillantes.</span><span class="sxs-lookup"><span data-stu-id="06808-128">Note also that link demands help protect against only the immediate callers and might still be subject to luring attacks.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="06808-129">Un nouveau modèle de transparence a été introduit dans le .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="06808-129">A new transparency model has been introduced in the .NET Framework 4.</span></span> <span data-ttu-id="06808-130">Le [code transparent de sécurité, le modèle de niveau 2](security-transparent-code-level-2.md) identifie le code sécurisé avec l' <xref:System.Security.SecurityCriticalAttribute> attribut.</span><span class="sxs-lookup"><span data-stu-id="06808-130">The [Security-Transparent Code, Level 2](security-transparent-code-level-2.md) model identifies secure code with the <xref:System.Security.SecurityCriticalAttribute> attribute.</span></span> <span data-ttu-id="06808-131">Le code critique de sécurité nécessite que les appelants et les héritiers soient entièrement fiables.</span><span class="sxs-lookup"><span data-stu-id="06808-131">Security-critical code requires both callers and inheritors to be fully trusted.</span></span> <span data-ttu-id="06808-132">Les assemblys qui s'exécutent selon les règles de sécurité d'accès du code des versions antérieures du .NET Framework peuvent appeler les assemblys de niveau 2.</span><span class="sxs-lookup"><span data-stu-id="06808-132">Assemblies that are running under the code access security rules from earlier .NET Framework versions can call level 2 assemblies.</span></span> <span data-ttu-id="06808-133">Dans ce cas, les attributs critiques de sécurité seront traités comme des demandes de liaison pour la confiance totale.</span><span class="sxs-lookup"><span data-stu-id="06808-133">In this case, the security-critical attributes will be treated as link demands for full trust.</span></span>  
  
 <span data-ttu-id="06808-134">Dans les assemblys avec nom fort, un [LinkDemand](link-demands.md) est appliqué à toutes les méthodes, propriétés et événements accessibles publiquement afin de limiter leur utilisation aux appelants d’un niveau de confiance suffisant.</span><span class="sxs-lookup"><span data-stu-id="06808-134">In strong-named assemblies, a [LinkDemand](link-demands.md) is applied to all publicly accessible methods, properties, and events therein to restrict their use to fully trusted callers.</span></span> <span data-ttu-id="06808-135">Pour désactiver cette fonctionnalité, vous devez appliquer l’attribut <xref:System.Security.AllowPartiallyTrustedCallersAttribute>.</span><span class="sxs-lookup"><span data-stu-id="06808-135">To disable this feature, you must apply the <xref:System.Security.AllowPartiallyTrustedCallersAttribute> attribute.</span></span> <span data-ttu-id="06808-136">De cette manière, marquer les classes de manière explicite afin d'exclure des appelants non fiables n'est nécessaire que pour des assemblys non signés ou des assemblys possédant cet attribut ; vous pouvez utiliser ces déclarations pour marquer un sous-ensemble de types qui ne sont pas destinés à des appelants non fiables.</span><span class="sxs-lookup"><span data-stu-id="06808-136">Thus, explicitly marking classes to exclude untrusted callers is necessary only for unsigned assemblies or assemblies with this attribute; you can use these declarations to mark a subset of types therein that are not intended for untrusted callers.</span></span>  
  
 <span data-ttu-id="06808-137">Les exemples suivants montrent comment empêcher des classes et des membres d'être utilisés par du code non fiable.</span><span class="sxs-lookup"><span data-stu-id="06808-137">The following examples show how to prevent classes and members from being used by untrusted code.</span></span>  
  
 <span data-ttu-id="06808-138">Pour les classes public non-sealed :</span><span class="sxs-lookup"><span data-stu-id="06808-138">For public nonsealed classes:</span></span>  
  
```vb  
<System.Security.Permissions.PermissionSetAttribute(System.Security.Permissions.SecurityAction.InheritanceDemand, Name := "FullTrust"), _
System.Security.Permissions.PermissionSetAttribute(System.Security.Permissions.SecurityAction.LinkDemand, Name := "FullTrust")>  _  
Public Class CanDeriveFromMe  
End Class  
```  
  
```csharp  
[System.Security.Permissions.PermissionSetAttribute(System.Security.Permissions.SecurityAction.InheritanceDemand, Name="FullTrust")]  
[System.Security.Permissions.PermissionSetAttribute(System.Security.Permissions.SecurityAction.LinkDemand, Name="FullTrust")]  
public class CanDeriveFromMe  
{  
}  
```  
  
 <span data-ttu-id="06808-139">Pour les classes public sealed :</span><span class="sxs-lookup"><span data-stu-id="06808-139">For public sealed classes:</span></span>  
  
```vb  
<System.Security.Permissions.PermissionSetAttribute(System.Security.Permissions.SecurityAction.LinkDemand, Name := "FullTrust")>  _  
NotInheritable Public Class CannotDeriveFromMe  
End Class  
```  
  
```csharp  
[System.Security.Permissions.PermissionSetAttribute(System.Security.Permissions.SecurityAction.LinkDemand, Name="FullTrust")]  
public sealed class CannotDeriveFromMe  
{  
}  
```  
  
 <span data-ttu-id="06808-140">Pour les classes public abstract :</span><span class="sxs-lookup"><span data-stu-id="06808-140">For public abstract classes:</span></span>  
  
```vb  
<System.Security.Permissions.PermissionSetAttribute(System.Security.Permissions.SecurityAction.InheritanceDemand, Name := "FullTrust"), _  
System.Security.Permissions.PermissionSetAttribute(System.Security.Permissions.SecurityAction.LinkDemand, Name := "FullTrust")>  _  
MustInherit Public Class CannotCreateInstanceOfMe_CanCastToMe  
End Class  
```  
  
```csharp  
[System.Security.Permissions.PermissionSetAttribute(System.Security.Permissions.SecurityAction.InheritanceDemand, Name="FullTrust")]  
[System.Security.Permissions.PermissionSetAttribute(System.Security.Permissions.SecurityAction.LinkDemand, Name="FullTrust")]  
public abstract class CannotCreateInstanceOfMe_CanCastToMe {}  
```  
  
 <span data-ttu-id="06808-141">Pour les fonctions virtuelles public :</span><span class="sxs-lookup"><span data-stu-id="06808-141">For public virtual functions:</span></span>  
  
```vb  
Class Base1
<System.Security.Permissions.PermissionSetAttribute(System.Security.Permissions.SecurityAction.InheritanceDemand, Name:="FullTrust"), System.Security.Permissions.PermissionSetAttribute(System.Security.Permissions.SecurityAction.LinkDemand, Name:="FullTrust")> _  
    Public Overridable Sub CanOverrideOrCallMe()  
    End Sub 'CanOverrideOrCallMe  
End Class 'Base1  
```  
  
```csharp  
class Base1
{  
[System.Security.Permissions.PermissionSetAttribute(  
System.Security.Permissions.SecurityAction.InheritanceDemand, Name="FullTrust")]  
[System.Security.Permissions.PermissionSetAttribute(  
System.Security.Permissions.SecurityAction.LinkDemand, Name="FullTrust")]  
    public virtual void CanOverrideOrCallMe() {}  
}  
```  
  
 <span data-ttu-id="06808-142">Pour les fonctions abstract public :</span><span class="sxs-lookup"><span data-stu-id="06808-142">For public abstract functions:</span></span>  
  
```vb  
MustInherit Class Base2  
    <System.Security.Permissions.PermissionSetAttribute(System.Security.Permissions.SecurityAction.InheritanceDemand, Name:="FullTrust"), System.Security.Permissions.PermissionSetAttribute(System.Security.Permissions.SecurityAction.LinkDemand, Name:="FullTrust")> _  
    Public Sub MustOverrideMe()  
    End Sub  
End Class 'Base2  
```  
  
```csharp  
abstract class Base2 {  
[System.Security.Permissions.PermissionSetAttribute(  
System.Security.Permissions.SecurityAction.InheritanceDemand, Name = "FullTrust")]  
[System.Security.Permissions.PermissionSetAttribute(  
System.Security.Permissions.SecurityAction.LinkDemand, Name = "FullTrust")]  
public abstract void MustOverrideMe();  
}  
```  
  
 <span data-ttu-id="06808-143">Pour des fonctions de substitution public où la classe de base n'exige pas la confiance totale :</span><span class="sxs-lookup"><span data-stu-id="06808-143">For public override functions where the base class does not demand full trust:</span></span>  
  
```vb  
Class Derived  
    Inherits Base1  
<System.Security.Permissions.PermissionSetAttribute(System.Security.Permissions.SecurityAction.Demand, Name:="FullTrust")> _  
    Public Overrides Sub CanOverrideOrCallMe()  
        MyBase.CanOverrideOrCallMe()  
    End Sub 'CanOverrideOrCallMe  
End Class 'Derived  
```  
  
```csharp  
class Derived : Base1  
{
[System.Security.Permissions.PermissionSetAttribute(System.Security.Permissions.SecurityAction.Demand, Name="FullTrust")]
    public override void CanOverrideOrCallMe()
    {  
        base.CanOverrideOrCallMe();  
    }  
}  
```  
  
 <span data-ttu-id="06808-144">Pour des fonctions de substitution public où la classe de base exige la confiance totale :</span><span class="sxs-lookup"><span data-stu-id="06808-144">For public override functions where the base class demands full trust:</span></span>  
  
```vb  
Class Derived  
    Inherits Base1  
<System.Security.Permissions.PermissionSetAttribute(System.Security.Permissions.SecurityAction.LinkDemand, Name:="FullTrust")> _  
    Public Overrides Sub CanOverrideOrCallMe()  
        MyBase.CanOverrideOrCallMe()  
    End Sub 'CanOverrideOrCallMe
End Class 'Derived  
```  
  
```csharp  
class Derived : Base1  
{
[System.Security.Permissions.PermissionSetAttribute(System.Security.Permissions.SecurityAction.LinkDemand, Name="FullTrust")]
    public override void CanOverrideOrCallMe()
    {  
        base.CanOverrideOrCallMe();  
    }  
}  
```  
  
 <span data-ttu-id="06808-145">Pour des interfaces public :</span><span class="sxs-lookup"><span data-stu-id="06808-145">For public interfaces:</span></span>  
  
```vb  
Public Interface ICanCastToMe  
    <System.Security.Permissions.PermissionSetAttribute(System.Security.Permissions.SecurityAction.LinkDemand, Name:="FullTrust"), System.Security.Permissions.PermissionSetAttribute(System.Security.Permissions.SecurityAction.InheritanceDemand, Name:="FullTrust")> _  
    Sub CanImplementMe()  
End Interface 'ICanCastToMe  
<System.Security.Permissions.PermissionSetAttribute(System.Security.Permissions.SecurityAction.LinkDemand, Name:="FullTrust"), System.Security.Permissions.PermissionSetAttribute(System.Security.Permissions.SecurityAction.InheritanceDemand, Name:="FullTrust")> _  
Class Implemented  
    Implements ICanCastToMe  
    Public Sub CanImplementMe()  
    End Sub 'CanImplementMe  
```  
  
```csharp  
public interface ICanCastToMe
{  
[System.Security.Permissions.PermissionSetAttribute(System.Security.Permissions.SecurityAction.LinkDemand, Name = "FullTrust")]  
[System.Security.Permissions.PermissionSetAttribute(System.Security.Permissions.SecurityAction.InheritanceDemand, Name = "FullTrust")]  
void CanImplementMe();  
}  
[System.Security.Permissions.PermissionSetAttribute(System.Security.Permissions.SecurityAction.LinkDemand, Name = "FullTrust")]  
[System.Security.Permissions.PermissionSetAttribute(System.Security.Permissions.SecurityAction.InheritanceDemand, Name = "FullTrust")]  
class Implemented : ICanCastToMe  
{  
    public void CanImplementMe()  
    {  
    }  
}  
```  
  
## <a name="virtual-internal-overrides-or-overloads-overridable-friend"></a><span data-ttu-id="06808-146">Méthodes de substitution Virtual Internal ou Overloads Overridable Friend</span><span class="sxs-lookup"><span data-stu-id="06808-146">Virtual Internal Overrides or Overloads Overridable Friend</span></span>  
  
> [!NOTE]
> <span data-ttu-id="06808-147">Cette section vous avertit des problèmes de sécurité lors de la déclaration d’une méthode en tant que `virtual` et `internal` ( `Overloads` `Overridable` `Friend` dans Visual Basic).</span><span class="sxs-lookup"><span data-stu-id="06808-147">This section warns about a security issue when declaring a method as both `virtual` and `internal` (`Overloads` `Overridable` `Friend` in Visual Basic).</span></span> <span data-ttu-id="06808-148">Cet avertissement s’applique uniquement aux versions 1,0 et 1,1 du .NET Framework. il ne s’applique pas aux versions ultérieures.</span><span class="sxs-lookup"><span data-stu-id="06808-148">This warning applies only to the .NET Framework versions 1.0 and 1.1, it does not apply to later versions.</span></span>  
  
 <span data-ttu-id="06808-149">Dans les versions 1,0 et 1,1 du .NET Framework, vous devez être conscient d’une nuance de l’accessibilité du système de type lorsque vous confirmez que votre code n’est pas disponible pour d’autres assemblys.</span><span class="sxs-lookup"><span data-stu-id="06808-149">In the .NET Framework versions 1.0 and 1.1, you must be aware of a nuance of the type system accessibility when confirming that your code is unavailable to other assemblies.</span></span> <span data-ttu-id="06808-150">Une méthode déclarée **Virtual** et **Internal** (**overloads Overridable Friend** dans Visual Basic) peut substituer l’entrée vtable de la classe parente et ne peut être utilisée qu’à partir du même assembly, car elle est interne.</span><span class="sxs-lookup"><span data-stu-id="06808-150">A method that is declared **virtual** and **internal** (**Overloads Overridable Friend** in Visual Basic) can override the parent class's vtable entry and can be used only from within the same assembly because it is internal.</span></span> <span data-ttu-id="06808-151">Toutefois, l’accessibilité pour la substitution est déterminée par le mot clé **Virtual** , et elle peut être substituée à partir d’un autre assembly à condition que ce code ait accès à la classe elle-même.</span><span class="sxs-lookup"><span data-stu-id="06808-151">However, the accessibility for overriding is determined by the **virtual** keyword, and this can be overridden from another assembly as long as that code has access to the class itself.</span></span> <span data-ttu-id="06808-152">Si la possibilité d’un remplacement présente un problème, utilisez la sécurité déclarative pour le corriger ou supprimez le mot clé **Virtual** s’il n’est pas strictement requis.</span><span class="sxs-lookup"><span data-stu-id="06808-152">If the possibility of an override presents a problem, use declarative security to fix it, or remove the **virtual** keyword if it is not strictly required.</span></span>  
  
 <span data-ttu-id="06808-153">Même si un compilateur de langage empêche ces substitutions avec une erreur de compilation, il est possible que le code écrit avec d’autres compilateurs soit substitué.</span><span class="sxs-lookup"><span data-stu-id="06808-153">Even if a language compiler prevents these overrides with a compilation error, it is possible for code written with other compilers to override.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="06808-154">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="06808-154">See also</span></span>

- [<span data-ttu-id="06808-155">Instructions de codage sécurisé</span><span class="sxs-lookup"><span data-stu-id="06808-155">Secure Coding Guidelines</span></span>](../../standard/security/secure-coding-guidelines.md)
