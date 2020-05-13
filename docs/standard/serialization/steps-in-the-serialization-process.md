---
title: Étapes du processus de sérialisation
description: Le processus de sérialisation commence lorsque la méthode Serialize est appelée sur un formateur. Cet article décrit la séquence d’événements.
ms.date: 08/07/2017
helpviewer_keywords:
- binary serialization, steps
- serialization, steps
ms.assetid: 4bcbc883-2a91-418f-b968-6c86a25e9737
ms.openlocfilehash: 1f749b9102182e78bc3fda436cf386a9f5759d5a
ms.sourcegitcommit: d6bd7903d7d46698e9d89d3725f3bb4876891aa3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/13/2020
ms.locfileid: "83379102"
---
# <a name="steps-in-the-serialization-process"></a><span data-ttu-id="7dcfb-104">Étapes du processus de sérialisation</span><span class="sxs-lookup"><span data-stu-id="7dcfb-104">Steps in the serialization process</span></span>
<span data-ttu-id="7dcfb-105">Quand la méthode <xref:System.Runtime.Serialization.Formatter.Serialize%2A> est appelée sur un [formateur](xref:System.Runtime.Serialization.Formatter), la sérialisation de l’objet s’effectue d’après la séquence de règles suivante :</span><span class="sxs-lookup"><span data-stu-id="7dcfb-105">When the <xref:System.Runtime.Serialization.Formatter.Serialize%2A> method is called on a [formatter](xref:System.Runtime.Serialization.Formatter), object serialization proceeds according to the following sequence of rules:</span></span>

- <span data-ttu-id="7dcfb-106">Un contrôle est effectué pour déterminer si le formateur possède un sélecteur de substitut.</span><span class="sxs-lookup"><span data-stu-id="7dcfb-106">A check is made to determine whether the formatter has a surrogate selector.</span></span> <span data-ttu-id="7dcfb-107">Si tel est le cas, vérifiez si le sélecteur de substitut gère des objets du type donné.</span><span class="sxs-lookup"><span data-stu-id="7dcfb-107">If the formatter does, check whether the surrogate selector handles objects of the given type.</span></span> <span data-ttu-id="7dcfb-108">Si le sélecteur gère le type d’objet, <xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A?displayProperty=nameWithType> est appelée sur le sélecteur de substitution.</span><span class="sxs-lookup"><span data-stu-id="7dcfb-108">If the selector handles the object type, <xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A?displayProperty=nameWithType> is called on the surrogate selector.</span></span>

- <span data-ttu-id="7dcfb-109">S’il n’existe aucun sélecteur de substitution ou s’il ne gère pas ce type d’objet, un contrôle est effectué pour déterminer si l’objet est marqué avec l’attribut [Serializable](xref:System.SerializableAttribute).</span><span class="sxs-lookup"><span data-stu-id="7dcfb-109">If there is no surrogate selector or if it does not handle the object type, a check is made to determine whether the object is marked with the [Serializable](xref:System.SerializableAttribute) attribute.</span></span> <span data-ttu-id="7dcfb-110">S’il ne l’est pas, une exception <xref:System.Runtime.Serialization.SerializationException> est levée.</span><span class="sxs-lookup"><span data-stu-id="7dcfb-110">If the object is not, a <xref:System.Runtime.Serialization.SerializationException> is thrown.</span></span>

- <span data-ttu-id="7dcfb-111">Si l’objet est marqué convenablement, vérifiez s’il implémente l’interface <xref:System.Runtime.Serialization.ISerializable>.</span><span class="sxs-lookup"><span data-stu-id="7dcfb-111">If the object is marked appropriately, check whether the object implements the <xref:System.Runtime.Serialization.ISerializable> interface.</span></span> <span data-ttu-id="7dcfb-112">Si tel est le cas, <xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A> est appelée sur l’objet.</span><span class="sxs-lookup"><span data-stu-id="7dcfb-112">If the object does, <xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A> is called on the object.</span></span>
  
- <span data-ttu-id="7dcfb-113">Si l’objet n’implémente pas <xref:System.Runtime.Serialization.ISerializable>, la stratégie de sérialisation par défaut est utilisée. Elle permet de sérialiser tous les champs non marqués comme [NonSerialized](xref:System.NonSerializedAttribute).</span><span class="sxs-lookup"><span data-stu-id="7dcfb-113">If the object does not implement <xref:System.Runtime.Serialization.ISerializable>, the default serialization policy is used, serializing all fields not marked as [NonSerialized](xref:System.NonSerializedAttribute).</span></span>

[!INCLUDE [binary-serialization-warning](../../../includes/binary-serialization-warning.md)]
  
## <a name="see-also"></a><span data-ttu-id="7dcfb-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="7dcfb-114">See also</span></span>

- [<span data-ttu-id="7dcfb-115">Sérialisation binaire</span><span class="sxs-lookup"><span data-stu-id="7dcfb-115">Binary Serialization</span></span>](binary-serialization.md)
- [<span data-ttu-id="7dcfb-116">Sérialisation XML et SOAP</span><span class="sxs-lookup"><span data-stu-id="7dcfb-116">XML and SOAP Serialization</span></span>](xml-and-soap-serialization.md)
