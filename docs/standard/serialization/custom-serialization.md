---
title: Sérialisation personnalisée
description: La sérialisation personnalisée contrôle la sérialisation et la désérialisation d’un type. Le contrôle de la sérialisation peut garantir la compatibilité de la sérialisation.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- binary serialization, custom serialization
- custom serialization
- binary serialization, controlling
- OptionalFieldAttribute class, custom serialization
- ISerializable interface, custom serialization
- OnDeserializingAttribute class, custom serialization
- OnSerializedAttribute class, custom serialization
- serialization, custom serialization
- serialization, controlling
- OnDeserializedAttribute class, custom serialization
- OnSerializingAttribute class, custom serialization
ms.assetid: 12ed422d-5280-49b8-9b71-a2ed129c0384
ms.openlocfilehash: 1532c4eeb09e7110d0f369ec47f342256889e576
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/02/2020
ms.locfileid: "84289653"
---
# <a name="custom-serialization"></a><span data-ttu-id="abb68-104">Sérialisation personnalisée</span><span class="sxs-lookup"><span data-stu-id="abb68-104">Custom serialization</span></span>
<span data-ttu-id="abb68-105">La sérialisation personnalisée est le processus de contrôle de la sérialisation et désérialisation d'un type.</span><span class="sxs-lookup"><span data-stu-id="abb68-105">Custom serialization is the process of controlling the serialization and deserialization of a type.</span></span> <span data-ttu-id="abb68-106">En contrôlant la sérialisation, il est possible de garantir la compatibilité de sérialisation (capacité de sérialisation et désérialisation entre des versions d’un type) sans interrompre la fonctionnalité principale du type.</span><span class="sxs-lookup"><span data-stu-id="abb68-106">By controlling serialization, it's possible to ensure serialization compatibility, which is the ability to serialize and deserialize between versions of a type without breaking the core functionality of the type.</span></span> <span data-ttu-id="abb68-107">Par exemple, il peut y avoir uniquement deux champs dans la première version d'un type.</span><span class="sxs-lookup"><span data-stu-id="abb68-107">For example, in the first version of a type, there may be only two fields.</span></span> <span data-ttu-id="abb68-108">Dans la version suivante d'un type, plusieurs champs supplémentaires sont ajoutés.</span><span class="sxs-lookup"><span data-stu-id="abb68-108">In the next version of a type, several more fields are added.</span></span> <span data-ttu-id="abb68-109">La deuxième version d'une application doit néanmoins être en mesure de sérialiser et désérialiser les deux types.</span><span class="sxs-lookup"><span data-stu-id="abb68-109">Yet the second version of an application must be able to serialize and deserialize both types.</span></span> <span data-ttu-id="abb68-110">Les sections suivantes décrivent comment contrôler la sérialisation.</span><span class="sxs-lookup"><span data-stu-id="abb68-110">The following sections describe how to control serialization.</span></span>

[!INCLUDE [binary-serialization-warning](../../../includes/binary-serialization-warning.md)]
  
> [!IMPORTANT]
> <span data-ttu-id="abb68-111">Dans les versions antérieures au .NET Framework 4.0, la sérialisation de données utilisateur personnalisées dans un assembly d’un niveau de confiance partiel était obtenue à l’aide de GetObjectData.</span><span class="sxs-lookup"><span data-stu-id="abb68-111">In versions previous to .NET Framework 4.0, serialization of custom user data in a partially trusted assembly was accomplished using the GetObjectData.</span></span> <span data-ttu-id="abb68-112">Depuis la version 4.0, cette méthode est marquée avec l'attribut <xref:System.Security.SecurityCriticalAttribute>, ce qui empêche l'exécution dans les assemblys d'un niveau de confiance partiel.</span><span class="sxs-lookup"><span data-stu-id="abb68-112">Starting with version 4.0, that method is marked with the <xref:System.Security.SecurityCriticalAttribute> attribute which prevents execution in partially trusted assemblies.</span></span> <span data-ttu-id="abb68-113">Pour contourner cette condition, implémentez l'interface <xref:System.Runtime.Serialization.ISafeSerializationData>.</span><span class="sxs-lookup"><span data-stu-id="abb68-113">To work around this condition, implement the <xref:System.Runtime.Serialization.ISafeSerializationData> interface.</span></span>  
  
## <a name="running-custom-methods-during-and-after-serialization"></a><span data-ttu-id="abb68-114">Exécution de méthodes personnalisées pendant et après la sérialisation</span><span class="sxs-lookup"><span data-stu-id="abb68-114">Running custom methods during and after serialization</span></span>  
 <span data-ttu-id="abb68-115">La méthode conseillée la plus simple (présentée dans la version 2.0 du .NET Framework) consiste à appliquer les attributs suivants aux méthodes utilisées pour corriger des données pendant et après la sérialisation :</span><span class="sxs-lookup"><span data-stu-id="abb68-115">The best practice and easiest way (introduced in version 2.0 of the .NET Framework) is to apply the following attributes to methods that are used to correct data during and after serialization:</span></span>  
  
- <xref:System.Runtime.Serialization.OnDeserializedAttribute>  
  
- <xref:System.Runtime.Serialization.OnDeserializingAttribute>  
  
- <xref:System.Runtime.Serialization.OnSerializedAttribute>  
  
- <xref:System.Runtime.Serialization.OnSerializingAttribute>  
  
 <span data-ttu-id="abb68-116">Ces attributs permettent au type de participer à l'une ou à l'ensemble des quatre phases des processus de sérialisation et de désérialisation.</span><span class="sxs-lookup"><span data-stu-id="abb68-116">These attributes allow the type to participate in any one of, or all four of the phases, of the serialization and deserialization processes.</span></span> <span data-ttu-id="abb68-117">Les attributs spécifient les méthodes du type qui doivent être invoquées pendant chaque phase.</span><span class="sxs-lookup"><span data-stu-id="abb68-117">The attributes specify the methods of the type that should be invoked during each phase.</span></span> <span data-ttu-id="abb68-118">Les méthodes n'accèdent pas au flux de données de sérialisation mais vous permettent en revanche de modifier l'objet avant et après la sérialisation, ou avant et après la désérialisation.</span><span class="sxs-lookup"><span data-stu-id="abb68-118">The methods do not access the serialization stream but instead allow you to alter the object before and after serialization, or before and after deserialization.</span></span> <span data-ttu-id="abb68-119">Les attributs peuvent être appliqués à tous les niveaux de la hiérarchie d'héritage de type, et chaque méthode est appelée dans la hiérarchie de la base au plus dérivé.</span><span class="sxs-lookup"><span data-stu-id="abb68-119">The attributes can be applied at all levels of the type inheritance hierarchy, and each method is called in the hierarchy from the base to the most derived.</span></span> <span data-ttu-id="abb68-120">Ce mécanisme évite la complexité et tous les problèmes résultant de l'implémentation de l'interface <xref:System.Runtime.Serialization.ISerializable> en rendant l'implémentation la plus dérivée responsable de la sérialisation et de la désérialisation.</span><span class="sxs-lookup"><span data-stu-id="abb68-120">This mechanism avoids the complexity and any resulting issues of implementing the <xref:System.Runtime.Serialization.ISerializable> interface by giving the responsibility for serialization and deserialization to the most derived implementation.</span></span> <span data-ttu-id="abb68-121">En outre, ce mécanisme permet aux formateurs d'ignorer le remplissage de champs et la récupération du flux de données de sérialisation.</span><span class="sxs-lookup"><span data-stu-id="abb68-121">Additionally, this mechanism allows the formatters to ignore the population of fields and retrieval from the serialization stream.</span></span> <span data-ttu-id="abb68-122">Pour obtenir des informations et des exemples concernant le contrôle de la sérialisation et de la désérialisation, cliquez sur l'un des liens précédents.</span><span class="sxs-lookup"><span data-stu-id="abb68-122">For details and examples of controlling serialization and deserialization, click any of the previous links.</span></span>  
  
 <span data-ttu-id="abb68-123">De plus, lorsque vous ajoutez un nouveau champ à un type sérialisable existant, appliquez l'attribut <xref:System.Runtime.Serialization.OptionalFieldAttribute> au champ.</span><span class="sxs-lookup"><span data-stu-id="abb68-123">In addition, when adding a new field to an existing serializable type, apply the <xref:System.Runtime.Serialization.OptionalFieldAttribute> attribute to the field.</span></span> <span data-ttu-id="abb68-124"><xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> et <xref:System.Runtime.Serialization.Formatters.Soap.SoapFormatter> ignorent l'absence du champ lorsqu'un flux de données dont le nouveau champ est manquant est traité.</span><span class="sxs-lookup"><span data-stu-id="abb68-124">The <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> and the <xref:System.Runtime.Serialization.Formatters.Soap.SoapFormatter> ignores the absence of the field when a stream that is missing the new field is processed.</span></span>  
  
## <a name="implementing-the-iserializable-interface"></a><span data-ttu-id="abb68-125">Implémentation de l’interface ISerializable</span><span class="sxs-lookup"><span data-stu-id="abb68-125">Implementing the ISerializable interface</span></span>  
 <span data-ttu-id="abb68-126">L’autre méthode permettant de contrôler la sérialisation s’effectue en implémentant l’interface <xref:System.Runtime.Serialization.ISerializable> sur un objet.</span><span class="sxs-lookup"><span data-stu-id="abb68-126">The other way to control serialization is achieved by implementing the <xref:System.Runtime.Serialization.ISerializable> interface on an object.</span></span> <span data-ttu-id="abb68-127">Toutefois, notez que la méthode de la section précédente remplace cette méthode pour contrôler la sérialisation.</span><span class="sxs-lookup"><span data-stu-id="abb68-127">Note, however, that the method in the previous section supersedes this method to control serialization.</span></span>  
  
 <span data-ttu-id="abb68-128">De plus, vous ne devez pas utiliser la sérialisation par défaut sur une classe marquée avec l’attribut [Serializable](xref:System.SerializableAttribute) et présentant une sécurité déclarative ou impérative au niveau de la classe ou sur ses constructeurs.</span><span class="sxs-lookup"><span data-stu-id="abb68-128">In addition, you should not use default serialization on a class that is marked with the [Serializable](xref:System.SerializableAttribute) attribute and has declarative or imperative security at the class level or on its constructors.</span></span> <span data-ttu-id="abb68-129">En revanche, ces classes doivent toujours implémenter l'interface <xref:System.Runtime.Serialization.ISerializable>.</span><span class="sxs-lookup"><span data-stu-id="abb68-129">Instead, these classes should always implement the <xref:System.Runtime.Serialization.ISerializable> interface.</span></span>  
  
 <span data-ttu-id="abb68-130">L’implémentation de <xref:System.Runtime.Serialization.ISerializable> implique l’implémentation de la méthode `GetObjectData` et l’utilisation d’un constructeur spécial quand l’objet est désérialisé.</span><span class="sxs-lookup"><span data-stu-id="abb68-130">Implementing <xref:System.Runtime.Serialization.ISerializable> involves implementing the `GetObjectData` method and a special constructor that is used when the object is deserialized.</span></span> <span data-ttu-id="abb68-131">L'exemple de code suivant indique comment implémenter <xref:System.Runtime.Serialization.ISerializable> sur la classe `MyObject` d'une section précédente.</span><span class="sxs-lookup"><span data-stu-id="abb68-131">The following sample code shows how to implement <xref:System.Runtime.Serialization.ISerializable> on the `MyObject` class from a previous section.</span></span>  
  
```csharp
[Serializable]
public class MyObject : ISerializable
{
    public int n1;
    public int n2;
    public String str;

    public MyObject()
    {
    }

    protected MyObject(SerializationInfo info, StreamingContext context)
    {
      n1 = info.GetInt32("i");
      n2 = info.GetInt32("j");
      str = info.GetString("k");
    }

    [SecurityPermissionAttribute(SecurityAction.Demand, SerializationFormatter = true)]
    public virtual void GetObjectData(SerializationInfo info, StreamingContext context)
    {
        info.AddValue("i", n1);
        info.AddValue("j", n2);
        info.AddValue("k", str);
    }
}
```

```vb
<Serializable()>  _
Public Class MyObject
    Implements ISerializable
    Public n1 As Integer
    Public n2 As Integer
    Public str As String

    Public Sub New()
    End Sub

    Protected Sub New(ByVal info As SerializationInfo, ByVal context As StreamingContext)
        n1 = info.GetInt32("i")
        n2 = info.GetInt32("j")
        str = info.GetString("k")
    End Sub 'New

    <SecurityPermissionAttribute(SecurityAction.Demand, SerializationFormatter := True)> _
    Public Overridable Sub GetObjectData(ByVal info As SerializationInfo, ByVal context As StreamingContext)
        info.AddValue("i", n1)
        info.AddValue("j", n2)
        info.AddValue("k", str)
    End Sub
End Class
```  
  
 <span data-ttu-id="abb68-132">Quand **GetObjectData** est appelé pendant la sérialisation, vous êtes chargé de remplir le <xref:System.Runtime.Serialization.SerializationInfo> fourni avec l’appel à méthode.</span><span class="sxs-lookup"><span data-stu-id="abb68-132">When **GetObjectData** is called during serialization, you are responsible for populating the <xref:System.Runtime.Serialization.SerializationInfo> provided with the method call.</span></span> <span data-ttu-id="abb68-133">Ajoutez les variables à sérialiser sous forme de paires de noms et de valeurs.</span><span class="sxs-lookup"><span data-stu-id="abb68-133">Add the variables to be serialized as name and value pairs.</span></span> <span data-ttu-id="abb68-134">Tout texte peut être utilisé comme nom.</span><span class="sxs-lookup"><span data-stu-id="abb68-134">Any text can be used as the name.</span></span> <span data-ttu-id="abb68-135">Vous pouvez décider quelles variables membres sont ajoutées au <xref:System.Runtime.Serialization.SerializationInfo>, à condition qu'il y ait suffisamment de données sérialisées pour restaurer l'objet pendant la désérialisation.</span><span class="sxs-lookup"><span data-stu-id="abb68-135">You have the freedom to decide which member variables are added to the <xref:System.Runtime.Serialization.SerializationInfo>, provided that sufficient data is serialized to restore the object during deserialization.</span></span> <span data-ttu-id="abb68-136">Les classes dérivées doivent appeler la méthode **GetObjectData** sur l’objet de base si ce dernier implémente <xref:System.Runtime.Serialization.ISerializable>.</span><span class="sxs-lookup"><span data-stu-id="abb68-136">Derived classes should call the **GetObjectData** method on the base object if the latter implements <xref:System.Runtime.Serialization.ISerializable>.</span></span>  
  
 <span data-ttu-id="abb68-137">Notez que la sérialisation peut permettre à un autre code d'afficher ou de modifier des données d'instance d'objet qui seraient autrement inaccessibles.</span><span class="sxs-lookup"><span data-stu-id="abb68-137">Note that serialization can allow other code to see or modify object instance data that is otherwise inaccessible.</span></span> <span data-ttu-id="abb68-138">Par conséquent, le code qui exécute la sérialisation exige [SecurityPermission](xref:System.Security.Permissions.SecurityPermissionAttribute) avec l’indicateur <xref:System.Security.Permissions.SecurityPermissionAttribute.SerializationFormatter> défini.</span><span class="sxs-lookup"><span data-stu-id="abb68-138">Therefore, code that performs serialization requires the [SecurityPermission](xref:System.Security.Permissions.SecurityPermissionAttribute) with the <xref:System.Security.Permissions.SecurityPermissionAttribute.SerializationFormatter> flag specified.</span></span> <span data-ttu-id="abb68-139">Dans le cadre de la stratégie par défaut, cette autorisation n'est pas accordée à du code téléchargé depuis Internet ou un intranet ; seul le code sur l'ordinateur local reçoit cette autorisation.</span><span class="sxs-lookup"><span data-stu-id="abb68-139">Under default policy, this permission is not given to Internet-downloaded or intranet code; only code on the local computer is granted this permission.</span></span> <span data-ttu-id="abb68-140">La méthode **GetObjectData** doit être protégée explicitement en exigeant [SecurityPermission](xref:System.Security.Permissions.SecurityPermissionAttribute) avec l’indicateur <xref:System.Security.Permissions.SecurityPermissionAttribute.SerializationFormatter> défini ou en exigeant d’autres autorisations qui permettent de protéger spécifiquement des données privées.</span><span class="sxs-lookup"><span data-stu-id="abb68-140">The **GetObjectData** method must be explicitly protected either by demanding the [SecurityPermission](xref:System.Security.Permissions.SecurityPermissionAttribute) with the <xref:System.Security.Permissions.SecurityPermissionAttribute.SerializationFormatter> flag specified or by demanding other permissions that specifically help protect private data.</span></span>  
  
 <span data-ttu-id="abb68-141">Si un champ privé stocke des informations sensibles, vous devez exiger les autorisations appropriées sur **GetObjectData** pour protéger les données.</span><span class="sxs-lookup"><span data-stu-id="abb68-141">If a private field stores sensitive information, you should demand the appropriate permissions on **GetObjectData** to protect the data.</span></span> <span data-ttu-id="abb68-142">Rappelez-vous que le code auquel a été attribuée l’autorisation [SecurityPermission](xref:System.Security.Permissions.SecurityPermissionAttribute) avec l’indicateur **SerializationFormatter** défini peut afficher et modifier les données stockées dans les champs privés.</span><span class="sxs-lookup"><span data-stu-id="abb68-142">Remember that code that has been granted [SecurityPermission](xref:System.Security.Permissions.SecurityPermissionAttribute) with the **SerializationFormatter** flag specified can view and modify the data stored in private fields.</span></span> <span data-ttu-id="abb68-143">Un appelant malveillant qui a obtenu l’autorisation [SecurityPermission](xref:System.Security.Permissions.SecurityPermissionAttribute) peut consulter des données telles que les emplacements de répertoire cachés ou les autorisations accordées, et utiliser ces données pour exploiter une faille de sécurité sur l’ordinateur.</span><span class="sxs-lookup"><span data-stu-id="abb68-143">A malicious caller granted this [SecurityPermission](xref:System.Security.Permissions.SecurityPermissionAttribute) can view data such as hidden directory locations or granted permissions and use the data to exploit a security vulnerability on the computer.</span></span> <span data-ttu-id="abb68-144">Pour obtenir une liste complète des indicateurs d’autorisation de sécurité que vous pouvez spécifier, consultez l’[énumération SecurityPermissionFlag](xref:System.Security.Permissions.SecurityPermissionFlag).</span><span class="sxs-lookup"><span data-stu-id="abb68-144">For a complete list of the security permission flags you can specify, see the [SecurityPermissionFlag Enumeration](xref:System.Security.Permissions.SecurityPermissionFlag).</span></span>  
  
 <span data-ttu-id="abb68-145">Il convient de souligner que quand <xref:System.Runtime.Serialization.ISerializable> est ajouté à une classe, vous devez implémenter **GetObjectData** et le constructeur spécial.</span><span class="sxs-lookup"><span data-stu-id="abb68-145">It's important to stress that when <xref:System.Runtime.Serialization.ISerializable> is added to a class you must implement both **GetObjectData** and the special constructor.</span></span> <span data-ttu-id="abb68-146">Le compilateur vous avertit si **GetObjectData** est manquant.</span><span class="sxs-lookup"><span data-stu-id="abb68-146">The compiler warns you if **GetObjectData** is missing.</span></span> <span data-ttu-id="abb68-147">Toutefois, parce qu'il est impossible de mettre en œuvre l'implémentation d'un constructeur, aucun avertissement n'est fourni si le constructeur est absent, et une exception est levée lorsqu'une tentative est faite pour désérialiser une classe sans le constructeur.</span><span class="sxs-lookup"><span data-stu-id="abb68-147">However, because it is impossible to enforce the implementation of a constructor, no warning is provided if the constructor is absent, and an exception is thrown when an attempt is made to deserialize a class without the constructor.</span></span>  
  
 <span data-ttu-id="abb68-148">La conception actuelle a priorité sur une méthode <xref:System.Runtime.Serialization.ISerializationSurrogate.SetObjectData%2A> pour contourner les problèmes potentiels de sécurité et de versioning.</span><span class="sxs-lookup"><span data-stu-id="abb68-148">The current design was favored above a <xref:System.Runtime.Serialization.ISerializationSurrogate.SetObjectData%2A> method to get around potential security and versioning problems.</span></span> <span data-ttu-id="abb68-149">Par exemple, une méthode `SetObjectData` doit être publique si elle est définie dans le cadre d’une interface. Ainsi, les utilisateurs doivent écrire du code pour éviter que la méthode **SetObjectData** soit appelée plusieurs fois.</span><span class="sxs-lookup"><span data-stu-id="abb68-149">For example, a `SetObjectData` method must be public if it is defined as part of an interface; thus users must write code to defend against having the **SetObjectData** method called multiple times.</span></span> <span data-ttu-id="abb68-150">Sinon, une application malveillante qui appelle la méthode **SetObjectData** sur un objet lors de l’exécution d’une opération peut provoquer des problèmes potentiels.</span><span class="sxs-lookup"><span data-stu-id="abb68-150">Otherwise, a malicious application that calls the **SetObjectData** method on an object in the process of executing an operation can cause potential problems.</span></span>  
  
 <span data-ttu-id="abb68-151">Pendant la désérialisation, <xref:System.Runtime.Serialization.SerializationInfo> est transmis à la classe à l'aide du constructeur prévu à cette fin.</span><span class="sxs-lookup"><span data-stu-id="abb68-151">During deserialization, <xref:System.Runtime.Serialization.SerializationInfo> is passed to the class using the constructor provided for this purpose.</span></span> <span data-ttu-id="abb68-152">Toutes les contraintes de visibilité imposées au constructeur sont ignorées lorsque l'objet est désérialisé. Vous pouvez donc marquer la classe comme publique, protégée, interne ou privée.</span><span class="sxs-lookup"><span data-stu-id="abb68-152">Any visibility constraints placed on the constructor are ignored when the object is deserialized; so you can mark the class as public, protected, internal, or private.</span></span> <span data-ttu-id="abb68-153">Toutefois, la méthode conseillée consiste à protéger le constructeur tant que la classe n'est pas scellée. Le cas échéant, le constructeur doit être marqué comme privé.</span><span class="sxs-lookup"><span data-stu-id="abb68-153">However, it is a best practice to make the constructor protected unless the class is sealed, in which case the constructor should be marked private.</span></span> <span data-ttu-id="abb68-154">Le constructeur doit également exécuter une validation de saisie complète.</span><span class="sxs-lookup"><span data-stu-id="abb68-154">The constructor should also perform thorough input validation.</span></span> <span data-ttu-id="abb68-155">Pour éviter une utilisation incorrecte par un code malveillant, le constructeur doit appliquer les mêmes vérifications de sécurité et autorisations nécessaires pour obtenir une instance de la classe utilisant tout autre constructeur.</span><span class="sxs-lookup"><span data-stu-id="abb68-155">To avoid misuse by malicious code, the constructor should enforce the same security checks and permissions required to obtain an instance of the class using any other constructor.</span></span> <span data-ttu-id="abb68-156">Si vous ne respectez pas cette recommandation, le code malveillant peut présérialiser un objet, obtenir le contrôle avec [SecurityPermission](xref:System.Security.Permissions.SecurityPermissionAttribute) avec l’indicateur <xref:System.Security.Permissions.SecurityPermissionAttribute.SerializationFormatter> défini, et désérialiser l’objet sur un ordinateur client en contournant toute sécurité qui aurait été appliquée pendant la construction d’instance standard à l’aide d’un constructeur public.</span><span class="sxs-lookup"><span data-stu-id="abb68-156">If you do not follow this recommendation, malicious code can preserialize an object, obtain control with the [SecurityPermission](xref:System.Security.Permissions.SecurityPermissionAttribute) with the <xref:System.Security.Permissions.SecurityPermissionAttribute.SerializationFormatter> flag specified and deserialize the object on a client computer bypassing any security that would have been applied during standard instance construction using a public constructor.</span></span>  
  
 <span data-ttu-id="abb68-157">Pour restaurer l'état de l'objet, récupérez simplement les valeurs des variables de <xref:System.Runtime.Serialization.SerializationInfo> à l'aide des noms utilisés pendant la sérialisation.</span><span class="sxs-lookup"><span data-stu-id="abb68-157">To restore the state of the object, simply retrieve the values of the variables from <xref:System.Runtime.Serialization.SerializationInfo> using the names used during serialization.</span></span> <span data-ttu-id="abb68-158">Si la classe de base implémente <xref:System.Runtime.Serialization.ISerializable>, le constructeur de base doit être appelé pour permettre à l'objet de base de restaurer ses variables.</span><span class="sxs-lookup"><span data-stu-id="abb68-158">If the base class implements <xref:System.Runtime.Serialization.ISerializable>, the base constructor should be called to allow the base object to restore its variables.</span></span>  
  
 <span data-ttu-id="abb68-159">Quand vous dérivez une nouvelle classe d’une classe qui implémente <xref:System.Runtime.Serialization.ISerializable>, la classe dérivée doit implémenter aussi bien le constructeur que la méthode **GetObjectData** si elle a des variables qui doivent être sérialisées.</span><span class="sxs-lookup"><span data-stu-id="abb68-159">When you derive a new class from one that implements <xref:System.Runtime.Serialization.ISerializable>, the derived class must implement both the constructor as well as the **GetObjectData** method if it has variables that need to be serialized.</span></span> <span data-ttu-id="abb68-160">L'exemple de code suivant illustre la procédure à l'aide de la classe `MyObject` montrée précédemment.</span><span class="sxs-lookup"><span data-stu-id="abb68-160">The following code example shows how this is done using the `MyObject` class shown previously.</span></span>  
  
```csharp
[Serializable]
public class ObjectTwo : MyObject
{
    public int num;

    public ObjectTwo()
      : base()
    {
    }

    protected ObjectTwo(SerializationInfo si, StreamingContext context)
      : base(si, context)
    {
        num = si.GetInt32("num");
    }

    [SecurityPermissionAttribute(SecurityAction.Demand, SerializationFormatter = true)]
    public override void GetObjectData(SerializationInfo si, StreamingContext context)
    {
        base.GetObjectData(si,context);
        si.AddValue("num", num);
    }
}
```

```vb
<Serializable()>  _
Public Class ObjectTwo
    Inherits MyObject
    Public num As Integer

    Public Sub New()

    End Sub

    Protected Sub New(ByVal si As SerializationInfo, _
    ByVal context As StreamingContext)
        MyBase.New(si, context)
        num = si.GetInt32("num")
    End Sub

    <SecurityPermissionAttribute(SecurityAction.Demand, SerializationFormatter := True)> _
    Public Overrides Sub GetObjectData(ByVal si As SerializationInfo, ByVal context As StreamingContext)
        MyBase.GetObjectData(si, context)
        si.AddValue("num", num)
    End Sub
End Class
```  
  
 <span data-ttu-id="abb68-161">N’oubliez pas d’appeler la classe de base dans le constructeur de désérialisation.</span><span class="sxs-lookup"><span data-stu-id="abb68-161">Don't forget to call the base class in the deserialization constructor.</span></span> <span data-ttu-id="abb68-162">Sinon, le constructeur de la classe de base n’est jamais appelé et l’objet n’est pas entièrement construit après la désérialisation.</span><span class="sxs-lookup"><span data-stu-id="abb68-162">If this isn't done, the constructor on the base class is never called, and the object is not fully constructed after deserialization.</span></span>  
  
 <span data-ttu-id="abb68-163">Les objets sont reconstruits à l'envers et les méthodes d'appel au cours de la désérialisation peuvent avoir des effets secondaires indésirables, car les méthodes appelées peuvent se rapporter aux références d'objet qui n'ont pas été désérialisées au moment de l'appel.</span><span class="sxs-lookup"><span data-stu-id="abb68-163">Objects are reconstructed from the inside out; and calling methods during deserialization can have undesirable side effects, because the methods called might refer to object references that have not been deserialized by the time the call is made.</span></span> <span data-ttu-id="abb68-164">Si la classe qui est désérialisée implémente <xref:System.Runtime.Serialization.IDeserializationCallback>, la méthode <xref:System.Runtime.Serialization.IDeserializationCallback.OnDeserialization%2A> est appelée automatiquement une fois le graphique d’objets entier désérialisé.</span><span class="sxs-lookup"><span data-stu-id="abb68-164">If the class being deserialized implements the <xref:System.Runtime.Serialization.IDeserializationCallback>, the <xref:System.Runtime.Serialization.IDeserializationCallback.OnDeserialization%2A> method is automatically called when the entire object graph has been deserialized.</span></span> <span data-ttu-id="abb68-165">À ce stade, tous les objets enfants référencés ont été restaurés complètement.</span><span class="sxs-lookup"><span data-stu-id="abb68-165">At this point, all the child objects referenced have been fully restored.</span></span> <span data-ttu-id="abb68-166">Une table de hachage est un exemple typique d'une classe difficile à désérialiser sans utiliser l'écouteur d'événements.</span><span class="sxs-lookup"><span data-stu-id="abb68-166">A hash table is a typical example of a class that is difficult to deserialize without using the event listener.</span></span> <span data-ttu-id="abb68-167">Il est facile de récupérer les clés et valeurs paires pendant la désérialisation, mais l'ajout de ces objets à la table de hachage peut provoquer des problèmes. En effet, il n'y a aucune garantie que les classes dérivées de la table de hachage sont désérialisées.</span><span class="sxs-lookup"><span data-stu-id="abb68-167">It is easy to retrieve the key and value pairs during deserialization, but adding these objects back to the hash table can cause problems, because there is no guarantee that classes that derived from the hash table have been deserialized.</span></span> <span data-ttu-id="abb68-168">Par conséquent, les méthodes d'appel sur une table de hachage ne sont pas recommandées à ce stade.</span><span class="sxs-lookup"><span data-stu-id="abb68-168">Calling methods on a hash table at this stage is therefore not advisable.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="abb68-169">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="abb68-169">See also</span></span>

- [<span data-ttu-id="abb68-170">Sérialisation binaire</span><span class="sxs-lookup"><span data-stu-id="abb68-170">Binary Serialization</span></span>](binary-serialization.md)
- [<span data-ttu-id="abb68-171">Sérialisation XML et SOAP</span><span class="sxs-lookup"><span data-stu-id="abb68-171">XML and SOAP Serialization</span></span>](xml-and-soap-serialization.md)
- [<span data-ttu-id="abb68-172">Sécurité et sérialisation</span><span class="sxs-lookup"><span data-stu-id="abb68-172">Security and Serialization</span></span>](../../framework/misc/security-and-serialization.md)
