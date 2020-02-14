---
title: Sécurité et sérialisation
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- code security, serialization
- serialization, security
- secure coding, serialization
- security [.NET Framework], serialization
ms.assetid: b921bc94-bd3a-4c91-9ede-2c8d4f78ea9a
ms.openlocfilehash: cb0ba120eeb57788c0525d45b714ad8edd2c39ed
ms.sourcegitcommit: 9c54866bcbdc49dbb981dd55be9bbd0443837aa2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/14/2020
ms.locfileid: "77216977"
---
# <a name="security-and-serialization"></a><span data-ttu-id="081b1-102">Sécurité et sérialisation</span><span class="sxs-lookup"><span data-stu-id="081b1-102">Security and Serialization</span></span>
<span data-ttu-id="081b1-103">Étant donné que la sérialisation peut permettre à tout autre code d’afficher ou de modifier les données d’instance d’objet qui seraient autrement inaccessibles, une autorisation spéciale est nécessaire pour que le code effectue la sérialisation : <xref:System.Security.Permissions.SecurityPermission> avec l’indicateur <xref:System.Security.Permissions.SecurityPermissionFlag.SerializationFormatter> spécifié.</span><span class="sxs-lookup"><span data-stu-id="081b1-103">Because serialization can allow other code to see or modify object instance data that would otherwise be inaccessible, a special permission is required of code performing serialization: <xref:System.Security.Permissions.SecurityPermission> with the <xref:System.Security.Permissions.SecurityPermissionFlag.SerializationFormatter> flag specified.</span></span> <span data-ttu-id="081b1-104">Dans le cadre de la stratégie par défaut, cette autorisation n'est pas accordée à du code téléchargé depuis Internet ou un intranet ; seul le code sur l'ordinateur local reçoit cette autorisation.</span><span class="sxs-lookup"><span data-stu-id="081b1-104">Under default policy, this permission is not given to Internet-downloaded or intranet code; only code on the local computer is granted this permission.</span></span>  
  
 <span data-ttu-id="081b1-105">Normalement, tous les champs d’une instance d’objet sont sérialisés, ce qui signifie que les données sont représentées dans les données sérialisées pour l’instance.</span><span class="sxs-lookup"><span data-stu-id="081b1-105">Normally, all fields of an object instance are serialized, meaning that data is represented in the serialized data for the instance.</span></span> <span data-ttu-id="081b1-106">Le code capable d’interpréter le format a la possibilité de déterminer la nature des valeurs de données, indépendamment de l’accessibilité du membre.</span><span class="sxs-lookup"><span data-stu-id="081b1-106">It is possible for code that can interpret the format to determine what the data values are, independent of the accessibility of the member.</span></span> <span data-ttu-id="081b1-107">De même, la désérialisation extrait des données de la représentation sérialisée et définit l’état de l’objet directement, encore une fois, quelles que soient les règles d’accessibilité.</span><span class="sxs-lookup"><span data-stu-id="081b1-107">Similarly, deserialization extracts data from the serialized representation and sets object state directly, again irrespective of accessibility rules.</span></span>  
  
 <span data-ttu-id="081b1-108">Si possible, tout objet pouvant contenir des données de sécurité sensibles doit être non sérialisable.</span><span class="sxs-lookup"><span data-stu-id="081b1-108">Any object that could contain security-sensitive data should be made nonserializable, if possible.</span></span> <span data-ttu-id="081b1-109">S’il doit être sérialisable, essayez de définir les champs spécifiques qui contiennent des données sensibles en tant que non sérialisables.</span><span class="sxs-lookup"><span data-stu-id="081b1-109">If it must be serializable, try to make specific fields that hold sensitive data nonserializable.</span></span> <span data-ttu-id="081b1-110">Si cette opération ne peut pas être effectuée, n’oubliez pas que ces données sont exposées à tout code ayant l’autorisation de sérialiser, et assurez-vous qu’aucun code malveillant ne peut obtenir cette autorisation.</span><span class="sxs-lookup"><span data-stu-id="081b1-110">If this cannot be done, be aware that this data will be exposed to any code that has permission to serialize, and make sure that no malicious code can get this permission.</span></span>  
  
 <span data-ttu-id="081b1-111">L’interface <xref:System.Runtime.Serialization.ISerializable> est conçue pour être utilisée uniquement par l’infrastructure de sérialisation.</span><span class="sxs-lookup"><span data-stu-id="081b1-111">The <xref:System.Runtime.Serialization.ISerializable> interface is intended for use only by the serialization infrastructure.</span></span> <span data-ttu-id="081b1-112">Toutefois, si elle est non protégée, elle risque de révéler des informations sensibles.</span><span class="sxs-lookup"><span data-stu-id="081b1-112">However, if unprotected, it can potentially release sensitive information.</span></span> <span data-ttu-id="081b1-113">Si vous fournissez une sérialisation personnalisée en implémentant **ISerializable**, veillez à prendre les précautions suivantes :</span><span class="sxs-lookup"><span data-stu-id="081b1-113">If you provide custom serialization by implementing **ISerializable**, make sure you take the following precautions:</span></span>  
  
- <span data-ttu-id="081b1-114">La méthode <xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A> doit être sécurisée de manière explicite en demandant l’autorisation **SecurityPermission** avec **SerializationFormatter** spécifié, ou en faisant en sorte qu’aucune information sensible ne soit divulguée avec la sortie de la méthode.</span><span class="sxs-lookup"><span data-stu-id="081b1-114">The <xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A> method should be explicitly secured either by demanding the **SecurityPermission** with **SerializationFormatter** permission specified or by making sure that no sensitive information is released with the method output.</span></span> <span data-ttu-id="081b1-115">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="081b1-115">For example:</span></span>  
  
    ```vb  
    Public Overrides<SecurityPermissionAttribute(SecurityAction.Demand, SerializationFormatter := True)>  _  
    Sub GetObjectData(info As SerializationInfo, context As StreamingContext)  
    End Sub  
    ```  
  
    ```csharp  
    [SecurityPermissionAttribute(SecurityAction.Demand,SerializationFormatter   
    =true)]  
    public override void GetObjectData(SerializationInfo info,   
    StreamingContext context)  
    {  
    }  
    ```  
  
- <span data-ttu-id="081b1-116">Le constructeur spécial utilisé pour la sérialisation doit également effectuer une validation de saisie complète et doit être protégé ou privé pour assurer la protection contre une mauvaise utilisation par du code malveillant.</span><span class="sxs-lookup"><span data-stu-id="081b1-116">The special constructor used for serialization should also perform thorough input validation and should be either protected or private to help protect against misuse by malicious code.</span></span> <span data-ttu-id="081b1-117">Il doit appliquer les mêmes vérifications de sécurité et autorisations nécessaires pour obtenir une instance de cette classe par d’autres moyens, par exemple, en créant explicitement la classe ou en la créant indirectement par le biais d’un type de fabrique.</span><span class="sxs-lookup"><span data-stu-id="081b1-117">It should enforce the same security checks and permissions required to obtain an instance of such a class by any other means, such as explicitly creating the class or indirectly creating it through some kind of factory.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="081b1-118">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="081b1-118">See also</span></span>

- [<span data-ttu-id="081b1-119">Instructions de codage sécurisé</span><span class="sxs-lookup"><span data-stu-id="081b1-119">Secure Coding Guidelines</span></span>](../../standard/security/secure-coding-guidelines.md)
