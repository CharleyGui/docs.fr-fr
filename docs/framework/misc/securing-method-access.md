---
title: Sécurisation de l'accès à la méthode
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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 8be971cee4aa2ae09745a090396269c80ca62198
ms.sourcegitcommit: 155012a8a826ee8ab6aa49b1b3a3b532e7b7d9bd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2019
ms.locfileid: "66487950"
---
# <a name="securing-method-access"></a><span data-ttu-id="c2ffe-102">Sécurisation de l'accès à la méthode</span><span class="sxs-lookup"><span data-stu-id="c2ffe-102">Securing Method Access</span></span>
[!INCLUDE[net_security_note](../../../includes/net-security-note-md.md)]  
  
 <span data-ttu-id="c2ffe-103">Il est possible que certaines méthodes ne conviennent pas à l'appel par du code arbitraire non fiable.</span><span class="sxs-lookup"><span data-stu-id="c2ffe-103">Some methods might not be suitable to allow arbitrary untrusted code to call.</span></span> <span data-ttu-id="c2ffe-104">Ces méthodes présentent plusieurs risques : La méthode peut fournir des informations restreintes ; elle peut croire aux informations transmises. Il peut ne pas faire la vérification d’erreurs sur les paramètres ; ou, avec des paramètres incorrects, il peut dysfonctionner ou quelque chose de dangereux.</span><span class="sxs-lookup"><span data-stu-id="c2ffe-104">Such methods pose several risks: The method might provide some restricted information; it might believe any information passed to it; it might not do error checking on the parameters; or with the wrong parameters, it might malfunction or do something harmful.</span></span> <span data-ttu-id="c2ffe-105">Vous devez connaître ces cas et adopter la bonne marche à suivre pour sécuriser la méthode.</span><span class="sxs-lookup"><span data-stu-id="c2ffe-105">You should be aware of these cases and take action to help protect the method.</span></span>  
  
 <span data-ttu-id="c2ffe-106">Dans certains cas, vous devrez peut-être limiter les méthodes qui ne sont pas destinées à une utilisation publique, mais qui doivent cependant être publiques.</span><span class="sxs-lookup"><span data-stu-id="c2ffe-106">In some cases, you might need to restrict methods that are not intended for public use but still must be public.</span></span> <span data-ttu-id="c2ffe-107">Par exemple, dans le cas d'une interface qui doit être appelée sur vos DLL, et donc être publique, celle-ci ne doit pas toutefois être exposée de manière publique afin d'empêcher son utilisation par des clients ou d'empêcher l'exploitation par du code nuisible du point d'entrée dans votre composant.</span><span class="sxs-lookup"><span data-stu-id="c2ffe-107">For example, you might have an interface that needs to be called across your own DLLs and hence must be public, but you do not want to expose it publicly to prevent customers from using it or to prevent malicious code from exploiting the entry point into your component.</span></span> <span data-ttu-id="c2ffe-108">Une autre raison courante de limiter une méthode qui n'est pas destinée à une utilisation publique (mais qui doit être publique) est d'éviter d'avoir à documenter et prendre en charge une interface qui peut se révéler très interne.</span><span class="sxs-lookup"><span data-stu-id="c2ffe-108">Another common reason to restrict a method not intended for public use (but that must be public) is to avoid having to document and support what might be a very internal interface.</span></span>  
  
 <span data-ttu-id="c2ffe-109">Le code managé propose plusieurs façons de limiter l'accès à la méthode :</span><span class="sxs-lookup"><span data-stu-id="c2ffe-109">Managed code offers several ways to restrict method access:</span></span>  
  
- <span data-ttu-id="c2ffe-110">Limitez l'étendue de l'accessibilité à la classe, à l'assembly ou aux classes dérivées, s'ils sont de confiance.</span><span class="sxs-lookup"><span data-stu-id="c2ffe-110">Limit the scope of accessibility to the class, assembly, or derived classes, if they can be trusted.</span></span> <span data-ttu-id="c2ffe-111">C'est la façon la plus simple de limiter l'accès à la méthode.</span><span class="sxs-lookup"><span data-stu-id="c2ffe-111">This is the simplest way to limit method access.</span></span> <span data-ttu-id="c2ffe-112">Notez que, en général, les classes dérivées peuvent être moins fiables que la classe dont elles dérivent, même si dans certains cas elles partagent l'identité de la classe parente.</span><span class="sxs-lookup"><span data-stu-id="c2ffe-112">Note that, in general, derived classes can be less trustworthy than the class they derive from, though in some cases they share the parent class's identity.</span></span> <span data-ttu-id="c2ffe-113">En particulier, ne déduisez pas un niveau de confiance du mot clé **protégé**, qui n’est pas nécessairement utilisé dans le contexte de sécurité.</span><span class="sxs-lookup"><span data-stu-id="c2ffe-113">In particular, do not infer trust from the keyword **protected**, which is not necessarily used in the security context.</span></span>  
  
- <span data-ttu-id="c2ffe-114">Limiter l’accès à la méthode aux appelants d’une identité spécifiée--essentiellement, n’importe quel [preuve](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/7y5x1hcd%28v=vs.100%29) (nom fort, éditeur, zone, etc.) que vous choisissez.</span><span class="sxs-lookup"><span data-stu-id="c2ffe-114">Limit the method access to callers of a specified identity--essentially, any particular [evidence](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/7y5x1hcd%28v=vs.100%29) (strong name, publisher, zone, and so on) you choose.</span></span>  
  
- <span data-ttu-id="c2ffe-115">Limitez l'accès à la méthode aux appelants dont les autorisations correspondent à celles que vous choisissez.</span><span class="sxs-lookup"><span data-stu-id="c2ffe-115">Limit the method access to callers having whatever permissions you select.</span></span>  
  
 <span data-ttu-id="c2ffe-116">De même, la sécurité déclarative vous permet de contrôler l'héritage de classes.</span><span class="sxs-lookup"><span data-stu-id="c2ffe-116">Similarly, declarative security allows you to control inheritance of classes.</span></span> <span data-ttu-id="c2ffe-117">Vous pouvez utiliser **InheritanceDemand** effectuer les opérations suivantes :</span><span class="sxs-lookup"><span data-stu-id="c2ffe-117">You can use **InheritanceDemand** to do the following:</span></span>  
  
- <span data-ttu-id="c2ffe-118">Obliger des classes dérivées à posséder une identité ou une autorisation spécifiée.</span><span class="sxs-lookup"><span data-stu-id="c2ffe-118">Require derived classes to have a specified identity or permission.</span></span>  
  
- <span data-ttu-id="c2ffe-119">Obliger des classes dérivées qui substituent des méthodes spécifiques à posséder une identité ou une autorisation spécifiée.</span><span class="sxs-lookup"><span data-stu-id="c2ffe-119">Require derived classes that override specific methods to have a specified identity or permission.</span></span>  
  
 <span data-ttu-id="c2ffe-120">L'exemple suivant montre comment sécuriser une classe public pour un accès limité en imposant que les appelants soient signés avec un nom fort particulier.</span><span class="sxs-lookup"><span data-stu-id="c2ffe-120">The following example shows how to help protect a public class for limited access by requiring that callers be signed with a particular strong name.</span></span> <span data-ttu-id="c2ffe-121">Cet exemple utilise le <xref:System.Security.Permissions.StrongNameIdentityPermissionAttribute> avec un **à la demande** pour le nom fort.</span><span class="sxs-lookup"><span data-stu-id="c2ffe-121">This example uses the <xref:System.Security.Permissions.StrongNameIdentityPermissionAttribute> with a **Demand** for the strong name.</span></span> <span data-ttu-id="c2ffe-122">Pour plus d’informations sur les tâches sur la façon de signer un assembly avec un nom fort, consultez [création et assemblys avec nom fort](../../../docs/framework/app-domains/create-and-use-strong-named-assemblies.md).</span><span class="sxs-lookup"><span data-stu-id="c2ffe-122">For task-based information on how to sign an assembly with a strong name, see [Creating and Using Strong-Named Assemblies](../../../docs/framework/app-domains/create-and-use-strong-named-assemblies.md).</span></span>  
  
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
  
## <a name="excluding-classes-and-members-from-use-by-untrusted-code"></a><span data-ttu-id="c2ffe-123">Exclusion des classes et des membres d'une utilisation par du code non fiable</span><span class="sxs-lookup"><span data-stu-id="c2ffe-123">Excluding Classes and Members from Use by Untrusted Code</span></span>  
 <span data-ttu-id="c2ffe-124">Utilisez les déclarations illustrées dans cette section pour empêcher des classes et des méthodes spécifiques, ainsi que des propriétés et des événements, d'être utilisés par du code d'un niveau de confiance partiel.</span><span class="sxs-lookup"><span data-stu-id="c2ffe-124">Use the declarations shown in this section to prevent specific classes and methods, as well as properties and events, from being used by partially trusted code.</span></span> <span data-ttu-id="c2ffe-125">En appliquant ces déclarations à une classe, vous appliquez la protection à toutes ses méthodes, propriétés et événements ; cependant, notez que l'accès au champ n'est pas affecté par la sécurité déclarative.</span><span class="sxs-lookup"><span data-stu-id="c2ffe-125">By applying these declarations to a class, you apply the protection to all its methods, properties, and events; however, note that field access is not affected by declarative security.</span></span> <span data-ttu-id="c2ffe-126">Notez également que les demandes de liaison ne protègent que contre les appelants immédiats et peuvent toujours faire l'objet d'attaques malveillantes.</span><span class="sxs-lookup"><span data-stu-id="c2ffe-126">Note also that link demands help protect against only the immediate callers and might still be subject to luring attacks.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="c2ffe-127">Un nouveau modèle de transparence a été introduit dans le .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="c2ffe-127">A new transparency model has been introduced in the .NET Framework 4.</span></span> <span data-ttu-id="c2ffe-128">Le [Code Transparent de sécurité, niveau 2](../../../docs/framework/misc/security-transparent-code-level-2.md) modèle identifie le code sécurisé avec le <xref:System.Security.SecurityCriticalAttribute> attribut.</span><span class="sxs-lookup"><span data-stu-id="c2ffe-128">The [Security-Transparent Code, Level 2](../../../docs/framework/misc/security-transparent-code-level-2.md) model identifies secure code with the <xref:System.Security.SecurityCriticalAttribute> attribute.</span></span> <span data-ttu-id="c2ffe-129">Le code critique de sécurité nécessite que les appelants et les héritiers soient entièrement fiables.</span><span class="sxs-lookup"><span data-stu-id="c2ffe-129">Security-critical code requires both callers and inheritors to be fully trusted.</span></span> <span data-ttu-id="c2ffe-130">Les assemblys qui s'exécutent selon les règles de sécurité d'accès du code des versions antérieures du .NET Framework peuvent appeler les assemblys de niveau 2.</span><span class="sxs-lookup"><span data-stu-id="c2ffe-130">Assemblies that are running under the code access security rules from earlier .NET Framework versions can call level 2 assemblies.</span></span> <span data-ttu-id="c2ffe-131">Dans ce cas, les attributs critiques de sécurité seront traités comme des demandes de liaison pour la confiance totale.</span><span class="sxs-lookup"><span data-stu-id="c2ffe-131">In this case, the security-critical attributes will be treated as link demands for full trust.</span></span>  
  
 <span data-ttu-id="c2ffe-132">Dans les assemblys avec nom fort, une [LinkDemand](../../../docs/framework/misc/link-demands.md) est appliqué à toutes les méthodes accessibles publiquement, des propriétés et des événements afin de limiter leur utilisation aux appelants de confiance totale.</span><span class="sxs-lookup"><span data-stu-id="c2ffe-132">In strong-named assemblies, a [LinkDemand](../../../docs/framework/misc/link-demands.md) is applied to all publicly accessible methods, properties, and events therein to restrict their use to fully trusted callers.</span></span> <span data-ttu-id="c2ffe-133">Pour désactiver cette fonctionnalité, vous devez appliquer l’attribut <xref:System.Security.AllowPartiallyTrustedCallersAttribute>.</span><span class="sxs-lookup"><span data-stu-id="c2ffe-133">To disable this feature, you must apply the <xref:System.Security.AllowPartiallyTrustedCallersAttribute> attribute.</span></span> <span data-ttu-id="c2ffe-134">De cette manière, marquer les classes de manière explicite afin d'exclure des appelants non fiables n'est nécessaire que pour des assemblys non signés ou des assemblys possédant cet attribut ; vous pouvez utiliser ces déclarations pour marquer un sous-ensemble de types qui ne sont pas destinés à des appelants non fiables.</span><span class="sxs-lookup"><span data-stu-id="c2ffe-134">Thus, explicitly marking classes to exclude untrusted callers is necessary only for unsigned assemblies or assemblies with this attribute; you can use these declarations to mark a subset of types therein that are not intended for untrusted callers.</span></span>  
  
 <span data-ttu-id="c2ffe-135">Les exemples suivants montrent comment empêcher des classes et des membres d'être utilisés par du code non fiable.</span><span class="sxs-lookup"><span data-stu-id="c2ffe-135">The following examples show how to prevent classes and members from being used by untrusted code.</span></span>  
  
 <span data-ttu-id="c2ffe-136">Pour les classes public non-sealed :</span><span class="sxs-lookup"><span data-stu-id="c2ffe-136">For public nonsealed classes:</span></span>  
  
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
  
 <span data-ttu-id="c2ffe-137">Pour les classes public sealed :</span><span class="sxs-lookup"><span data-stu-id="c2ffe-137">For public sealed classes:</span></span>  
  
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
  
 <span data-ttu-id="c2ffe-138">Pour les classes public abstract :</span><span class="sxs-lookup"><span data-stu-id="c2ffe-138">For public abstract classes:</span></span>  
  
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
  
 <span data-ttu-id="c2ffe-139">Pour les fonctions virtuelles public :</span><span class="sxs-lookup"><span data-stu-id="c2ffe-139">For public virtual functions:</span></span>  
  
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
  
 <span data-ttu-id="c2ffe-140">Pour les fonctions abstract public :</span><span class="sxs-lookup"><span data-stu-id="c2ffe-140">For public abstract functions:</span></span>  
  
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
  
 <span data-ttu-id="c2ffe-141">Pour des fonctions de substitution public où la classe de base n'exige pas la confiance totale :</span><span class="sxs-lookup"><span data-stu-id="c2ffe-141">For public override functions where the base class does not demand full trust:</span></span>  
  
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
  
 <span data-ttu-id="c2ffe-142">Pour des fonctions de substitution public où la classe de base exige la confiance totale :</span><span class="sxs-lookup"><span data-stu-id="c2ffe-142">For public override functions where the base class demands full trust:</span></span>  
  
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
  
 <span data-ttu-id="c2ffe-143">Pour des interfaces public :</span><span class="sxs-lookup"><span data-stu-id="c2ffe-143">For public interfaces:</span></span>  
  
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
  
## <a name="virtual-internal-overrides-or-overloads-overridable-friend"></a><span data-ttu-id="c2ffe-144">Méthodes de substitution Virtual Internal ou Overloads Overridable Friend</span><span class="sxs-lookup"><span data-stu-id="c2ffe-144">Virtual Internal Overrides or Overloads Overridable Friend</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="c2ffe-145">Cette section signale un problème de sécurité lorsque vous déclarez une méthode à la fois comme `virtual` et `internal` (`Overloads` `Overridable` `Friend` en Visual Basic).</span><span class="sxs-lookup"><span data-stu-id="c2ffe-145">This section warns about a security issue when declaring a method as both `virtual` and `internal` (`Overloads` `Overridable` `Friend` in Visual Basic).</span></span> <span data-ttu-id="c2ffe-146">Cet avertissement s’applique uniquement aux versions de .NET Framework 1.0 et 1.1, il ne s’applique pas aux versions ultérieures.</span><span class="sxs-lookup"><span data-stu-id="c2ffe-146">This warning applies only to the .NET Framework versions 1.0 and 1.1, it does not apply to later versions.</span></span>  
  
 <span data-ttu-id="c2ffe-147">Dans les versions 1.0 et 1.1 du .NET Framework, vous devez connaître une nuance de l’accessibilité du système de type lors de la confirmation que votre code n’est pas disponible aux autres assemblys.</span><span class="sxs-lookup"><span data-stu-id="c2ffe-147">In the .NET Framework versions 1.0 and 1.1, you must be aware of a nuance of the type system accessibility when confirming that your code is unavailable to other assemblies.</span></span> <span data-ttu-id="c2ffe-148">Une méthode qui est déclarée **virtuels** et **interne** (**Overloads Overridable Friend** en Visual Basic) peut substituer l’entrée vtable de la classe parente et peut être utilisé uniquement à partir de dans le même assembly, car il est interne.</span><span class="sxs-lookup"><span data-stu-id="c2ffe-148">A method that is declared **virtual** and **internal** (**Overloads Overridable Friend** in Visual Basic) can override the parent class's vtable entry and can be used only from within the same assembly because it is internal.</span></span> <span data-ttu-id="c2ffe-149">Toutefois, l’accessibilité permettant les substitutions est déterminée par le **virtuel** mot clé, qui peut être substituée à partir d’un autre assembly tant que ce code a accès à la classe elle-même.</span><span class="sxs-lookup"><span data-stu-id="c2ffe-149">However, the accessibility for overriding is determined by the **virtual** keyword, and this can be overridden from another assembly as long as that code has access to the class itself.</span></span> <span data-ttu-id="c2ffe-150">Si la possibilité d’une substitution présente un problème, utilisez la sécurité déclarative pour corriger ou supprimer la **virtuel** mot clé si elle n’est pas strictement obligatoire.</span><span class="sxs-lookup"><span data-stu-id="c2ffe-150">If the possibility of an override presents a problem, use declarative security to fix it, or remove the **virtual** keyword if it is not strictly required.</span></span>  
  
 <span data-ttu-id="c2ffe-151">Notez que même si un compilateur de langage empêche ces substitutions par une erreur de compilation, la substitution avec du code écrit avec d'autres compilateurs est possible.</span><span class="sxs-lookup"><span data-stu-id="c2ffe-151">Note that even if a language compiler prevents these overrides with a compilation error, it is possible for code written with other compilers to override.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c2ffe-152">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="c2ffe-152">See also</span></span>

- [<span data-ttu-id="c2ffe-153">Instructions de codage sécurisé</span><span class="sxs-lookup"><span data-stu-id="c2ffe-153">Secure Coding Guidelines</span></span>](../../../docs/standard/security/secure-coding-guidelines.md)
