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
ms.openlocfilehash: f9b9bc00058aefc8f58facff43509e717967c2a7
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90555716"
---
# <a name="securing-method-access"></a>Sécurisation de l'accès à la méthode

[!INCLUDE[net_security_note](../../../includes/net-security-note-md.md)]  
  
 Il est possible que certaines méthodes ne conviennent pas à l'appel par du code arbitraire non fiable. Ces méthodes présentent plusieurs risques : la méthode peut fournir des informations restreintes ; elle peut croire aux informations qui lui sont passées ; elle peut ne pas faire de vérification d'erreurs sur les paramètres ; ou dans le cas de paramètres erronés, la méthode peut dysfonctionner ou avoir des effets préjudiciables. Vous devez connaître ces cas et adopter la bonne marche à suivre pour sécuriser la méthode.  
  
 Dans certains cas, vous devrez peut-être limiter les méthodes qui ne sont pas destinées à une utilisation publique, mais qui doivent cependant être publiques. Par exemple, dans le cas d'une interface qui doit être appelée sur vos DLL, et donc être publique, celle-ci ne doit pas toutefois être exposée de manière publique afin d'empêcher son utilisation par des clients ou d'empêcher l'exploitation par du code nuisible du point d'entrée dans votre composant. Une autre raison courante de restreindre une méthode non destinée à une utilisation publique (mais qui doit être publique) consiste à éviter d’avoir à documenter et à prendre en charge ce qui peut être une interface interne.  
  
 Le code managé propose plusieurs façons de limiter l'accès à la méthode :  
  
- Limitez l'étendue de l'accessibilité à la classe, à l'assembly ou aux classes dérivées, s'ils sont de confiance. C'est la façon la plus simple de limiter l'accès à la méthode. En général, les classes dérivées peuvent être moins dignes de confiance que la classe à partir de laquelle elles dérivent, mais dans certains cas, elles partagent l’identité de la classe parente. En particulier, ne déduisez pas l’approbation à partir du mot clé `protected` , qui n’est pas nécessairement utilisé dans le contexte de sécurité.  
  
- Limitez l’accès à la méthode aux appelants d’une identité spécifiée (essentiellement, toute [preuve](/previous-versions/dotnet/netframework-4.0/7y5x1hcd(v=vs.100)) particulière (nom fort, éditeur, zone, etc.) que vous choisissez.  
  
- Limitez l'accès à la méthode aux appelants dont les autorisations correspondent à celles que vous choisissez.  
  
 De même, la sécurité déclarative vous permet de contrôler l'héritage de classes. Vous pouvez utiliser **InheritanceDemand** pour effectuer les opérations suivantes :  
  
- Obliger des classes dérivées à posséder une identité ou une autorisation spécifiée.  
  
- Obliger des classes dérivées qui substituent des méthodes spécifiques à posséder une identité ou une autorisation spécifiée.  
  
 L'exemple suivant montre comment sécuriser une classe public pour un accès limité en imposant que les appelants soient signés avec un nom fort particulier. Cet exemple utilise le <xref:System.Security.Permissions.StrongNameIdentityPermissionAttribute> avec une **demande** pour le nom fort. Pour obtenir des informations sur les tâches relatives à la signature d’un assembly avec un nom fort, consultez [création et utilisation d’assemblys](../../standard/assembly/create-use-strong-named.md)avec nom fort.  
  
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
  
## <a name="excluding-classes-and-members-from-use-by-untrusted-code"></a>Exclusion des classes et des membres d'une utilisation par du code non fiable  
 Utilisez les déclarations illustrées dans cette section pour empêcher des classes et des méthodes spécifiques, ainsi que des propriétés et des événements, d'être utilisés par du code d'un niveau de confiance partiel. En appliquant ces déclarations à une classe, vous appliquez la protection à toutes ses méthodes, propriétés et événements. Toutefois, l’accès au champ n’est pas affecté par la sécurité déclarative. Notez également que les demandes de liaison ne protègent que contre les appelants immédiats et peuvent toujours faire l'objet d'attaques malveillantes.  
  
> [!NOTE]
> Un nouveau modèle de transparence a été introduit dans le .NET Framework 4. Le [code transparent de sécurité, le modèle de niveau 2](security-transparent-code-level-2.md) identifie le code sécurisé avec l' <xref:System.Security.SecurityCriticalAttribute> attribut. Le code critique de sécurité nécessite que les appelants et les héritiers soient entièrement fiables. Les assemblys qui s'exécutent selon les règles de sécurité d'accès du code des versions antérieures du .NET Framework peuvent appeler les assemblys de niveau 2. Dans ce cas, les attributs critiques de sécurité seront traités comme des demandes de liaison pour la confiance totale.  
  
 Dans les assemblys avec nom fort, un [LinkDemand](link-demands.md) est appliqué à toutes les méthodes, propriétés et événements accessibles publiquement afin de limiter leur utilisation aux appelants d’un niveau de confiance suffisant. Pour désactiver cette fonctionnalité, vous devez appliquer l’attribut <xref:System.Security.AllowPartiallyTrustedCallersAttribute>. De cette manière, marquer les classes de manière explicite afin d'exclure des appelants non fiables n'est nécessaire que pour des assemblys non signés ou des assemblys possédant cet attribut ; vous pouvez utiliser ces déclarations pour marquer un sous-ensemble de types qui ne sont pas destinés à des appelants non fiables.  
  
 Les exemples suivants montrent comment empêcher des classes et des membres d'être utilisés par du code non fiable.  
  
 Pour les classes public non-sealed :  
  
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
  
 Pour les classes public sealed :  
  
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
  
 Pour les classes public abstract :  
  
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
  
 Pour les fonctions virtuelles public :  
  
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
  
 Pour les fonctions abstract public :  
  
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
  
 Pour des fonctions de substitution public où la classe de base n'exige pas la confiance totale :  
  
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
  
 Pour des fonctions de substitution public où la classe de base exige la confiance totale :  
  
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
  
 Pour des interfaces public :  
  
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
  
## <a name="virtual-internal-overrides-or-overloads-overridable-friend"></a>Méthodes de substitution Virtual Internal ou Overloads Overridable Friend  
  
> [!NOTE]
> Cette section vous avertit des problèmes de sécurité lors de la déclaration d’une méthode en tant que `virtual` et `internal` ( `Overloads` `Overridable` `Friend` dans Visual Basic). Cet avertissement s’applique uniquement aux versions 1,0 et 1,1 du .NET Framework. il ne s’applique pas aux versions ultérieures.  
  
 Dans les versions 1,0 et 1,1 du .NET Framework, vous devez être conscient d’une nuance de l’accessibilité du système de type lorsque vous confirmez que votre code n’est pas disponible pour d’autres assemblys. Une méthode déclarée **Virtual** et **Internal** (**overloads Overridable Friend** dans Visual Basic) peut substituer l’entrée vtable de la classe parente et ne peut être utilisée qu’à partir du même assembly, car elle est interne. Toutefois, l’accessibilité pour la substitution est déterminée par le mot clé **Virtual** , et elle peut être substituée à partir d’un autre assembly à condition que ce code ait accès à la classe elle-même. Si la possibilité d’un remplacement présente un problème, utilisez la sécurité déclarative pour le corriger ou supprimez le mot clé **Virtual** s’il n’est pas strictement requis.  
  
 Même si un compilateur de langage empêche ces substitutions avec une erreur de compilation, il est possible que le code écrit avec d’autres compilateurs soit substitué.  
  
## <a name="see-also"></a>Voir aussi

- [Instructions de codage sécurisé](../../standard/security/secure-coding-guidelines.md)
