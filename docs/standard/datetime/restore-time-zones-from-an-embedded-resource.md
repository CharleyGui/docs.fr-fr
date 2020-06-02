---
title: 'Procédure : restaurer des fuseaux horaires à partir d’une ressource incorporée'
ms.date: 04/10/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- time zones [.NET Framework], deserializing
- time zones [.NET Framework], restoring
ms.assetid: 6b7b4de9-da07-47e3-8f4c-823f81798ee7
ms.openlocfilehash: b1cece13c88b3a49c9c4c90045a07dd009d4282d
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/02/2020
ms.locfileid: "84281321"
---
# <a name="how-to-restore-time-zones-from-an-embedded-resource"></a><span data-ttu-id="97d71-102">Procédure : restaurer des fuseaux horaires à partir d’une ressource incorporée</span><span class="sxs-lookup"><span data-stu-id="97d71-102">How to: Restore time zones from an embedded resource</span></span>

<span data-ttu-id="97d71-103">Cette rubrique explique comment restaurer des fuseaux horaires qui ont été enregistrés dans un fichier de ressources.</span><span class="sxs-lookup"><span data-stu-id="97d71-103">This topic describes how to restore time zones that have been saved in a resource file.</span></span> <span data-ttu-id="97d71-104">Pour obtenir des informations et des instructions sur l’enregistrement des fuseaux horaires, consultez [Comment : enregistrer des fuseaux horaires dans une ressource incorporée](save-time-zones-to-an-embedded-resource.md).</span><span class="sxs-lookup"><span data-stu-id="97d71-104">For information and instructions about saving time zones, see [How to: Save time zones to an embedded resource](save-time-zones-to-an-embedded-resource.md).</span></span>

### <a name="to-deserialize-a-timezoneinfo-object-from-an-embedded-resource"></a><span data-ttu-id="97d71-105">Pour désérialiser un objet TimeZoneInfo à partir d’une ressource incorporée</span><span class="sxs-lookup"><span data-stu-id="97d71-105">To deserialize a TimeZoneInfo object from an embedded resource</span></span>

1. <span data-ttu-id="97d71-106">Si le fuseau horaire à récupérer n’est pas un fuseau horaire personnalisé, essayez de l’instancier à l’aide de la <xref:System.TimeZoneInfo.FindSystemTimeZoneById%2A> méthode.</span><span class="sxs-lookup"><span data-stu-id="97d71-106">If the time zone to be retrieved is not a custom time zone, try to instantiate it by using the <xref:System.TimeZoneInfo.FindSystemTimeZoneById%2A> method.</span></span>

2. <span data-ttu-id="97d71-107">Instanciez un <xref:System.Resources.ResourceManager> objet en passant le nom qualifié complet du fichier de ressources incorporé et une référence à l’assembly qui contient le fichier de ressources.</span><span class="sxs-lookup"><span data-stu-id="97d71-107">Instantiate a <xref:System.Resources.ResourceManager> object by passing the fully qualified name of the embedded resource file and a reference to the assembly that contains the resource file.</span></span>

   <span data-ttu-id="97d71-108">Si vous ne pouvez pas déterminer le nom complet du fichier de ressources incorporé, utilisez [Ildasm. exe (Désassembleur il)](../../framework/tools/ildasm-exe-il-disassembler.md) pour examiner le manifeste de l’assembly.</span><span class="sxs-lookup"><span data-stu-id="97d71-108">If you cannot determine the fully qualified name of the embedded resource file, use the [Ildasm.exe (IL Disassembler)](../../framework/tools/ildasm-exe-il-disassembler.md) to examine the assembly's manifest.</span></span> <span data-ttu-id="97d71-109">Une `.mresource` entrée identifie la ressource.</span><span class="sxs-lookup"><span data-stu-id="97d71-109">An `.mresource` entry identifies the resource.</span></span> <span data-ttu-id="97d71-110">Dans l’exemple, le nom complet de la ressource est `SerializeTimeZoneData.SerializedTimeZones` .</span><span class="sxs-lookup"><span data-stu-id="97d71-110">In the example, the resource's fully qualified name is `SerializeTimeZoneData.SerializedTimeZones`.</span></span>

   <span data-ttu-id="97d71-111">Si le fichier de ressources est incorporé dans le même assembly qui contient le code d’instanciation du fuseau horaire, vous pouvez récupérer une référence à celui-ci en appelant la `static` `Shared` méthode (en Visual Basic) <xref:System.Reflection.Assembly.GetExecutingAssembly%2A> .</span><span class="sxs-lookup"><span data-stu-id="97d71-111">If the resource file is embedded in the same assembly that contains the time zone instantiation code, you can retrieve a reference to it by calling the `static` (`Shared` in Visual Basic) <xref:System.Reflection.Assembly.GetExecutingAssembly%2A> method.</span></span>

3. <span data-ttu-id="97d71-112">Si l’appel à la <xref:System.TimeZoneInfo.FindSystemTimeZoneById%2A> méthode échoue, ou si un fuseau horaire personnalisé doit être instancié, récupérez une chaîne qui contient le fuseau horaire sérialisé en appelant la <xref:System.Resources.ResourceManager.GetString%2A?displayProperty=nameWithType> méthode.</span><span class="sxs-lookup"><span data-stu-id="97d71-112">If the call to the <xref:System.TimeZoneInfo.FindSystemTimeZoneById%2A> method fails, or if a custom time zone is to be instantiated, retrieve a string that contains the serialized time zone by calling the <xref:System.Resources.ResourceManager.GetString%2A?displayProperty=nameWithType> method.</span></span>

4. <span data-ttu-id="97d71-113">Désérialisez les données de fuseau horaire en appelant la <xref:System.TimeZoneInfo.FromSerializedString%2A> méthode.</span><span class="sxs-lookup"><span data-stu-id="97d71-113">Deserialize the time zone data by calling the <xref:System.TimeZoneInfo.FromSerializedString%2A> method.</span></span>

## <a name="example"></a><span data-ttu-id="97d71-114">Exemple</span><span class="sxs-lookup"><span data-stu-id="97d71-114">Example</span></span>

<span data-ttu-id="97d71-115">L’exemple suivant désérialise un <xref:System.TimeZoneInfo> objet stocké dans un fichier de ressources XML .net incorporé.</span><span class="sxs-lookup"><span data-stu-id="97d71-115">The following example deserializes a <xref:System.TimeZoneInfo> object stored in an embedded .NET XML resource file.</span></span>

[!code-csharp[TimeZone2.Serialization#3](../../../samples/snippets/csharp/VS_Snippets_CLR/TimeZone2.Serialization/cs/SerializeTimeZoneData.cs#3)]
[!code-vb[TimeZone2.Serialization#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/TimeZone2.Serialization/vb/SerializeTimeZoneData.vb#3)]

<span data-ttu-id="97d71-116">Ce code illustre la gestion des exceptions pour s’assurer qu’un <xref:System.TimeZoneInfo> objet requis par l’application est présent.</span><span class="sxs-lookup"><span data-stu-id="97d71-116">This code illustrates exception handling to ensure that a <xref:System.TimeZoneInfo> object required by the application is present.</span></span> <span data-ttu-id="97d71-117">Il tente d’abord d’instancier un <xref:System.TimeZoneInfo> objet en le récupérant à partir du Registre à l’aide de la <xref:System.TimeZoneInfo.FindSystemTimeZoneById%2A> méthode.</span><span class="sxs-lookup"><span data-stu-id="97d71-117">It first tries to instantiate a <xref:System.TimeZoneInfo> object by retrieving it from the registry using the <xref:System.TimeZoneInfo.FindSystemTimeZoneById%2A> method.</span></span> <span data-ttu-id="97d71-118">Si le fuseau horaire ne peut pas être instancié, le code le récupère à partir du fichier de ressources incorporé.</span><span class="sxs-lookup"><span data-stu-id="97d71-118">If the time zone cannot be instantiated, the code retrieves it from the embedded resource file.</span></span>

<span data-ttu-id="97d71-119">Étant donné que les données des fuseaux horaires personnalisés (fuseaux horaires instanciés à l’aide de la <xref:System.TimeZoneInfo.CreateCustomTimeZone%2A> méthode) ne sont pas stockées dans le registre, le code n’appelle pas <xref:System.TimeZoneInfo.FindSystemTimeZoneById%2A> pour instancier le fuseau horaire pour Palmer, Antarctique.</span><span class="sxs-lookup"><span data-stu-id="97d71-119">Because data for custom time zones (time zones instantiated by using the <xref:System.TimeZoneInfo.CreateCustomTimeZone%2A> method) are not stored in the registry, the code does not call the <xref:System.TimeZoneInfo.FindSystemTimeZoneById%2A> to instantiate the time zone for Palmer, Antarctica.</span></span> <span data-ttu-id="97d71-120">Au lieu de cela, il consulte immédiatement le fichier de ressources incorporé pour récupérer une chaîne qui contient les données du fuseau horaire avant d’appeler la <xref:System.TimeZoneInfo.FromSerializedString%2A> méthode.</span><span class="sxs-lookup"><span data-stu-id="97d71-120">Instead, it immediately looks to the embedded resource file to retrieve a string that contains the time zone's data before it calls the <xref:System.TimeZoneInfo.FromSerializedString%2A> method.</span></span>

## <a name="compiling-the-code"></a><span data-ttu-id="97d71-121">Compilation du code</span><span class="sxs-lookup"><span data-stu-id="97d71-121">Compiling the code</span></span>

<span data-ttu-id="97d71-122">Cet exemple nécessite :</span><span class="sxs-lookup"><span data-stu-id="97d71-122">This example requires:</span></span>

- <span data-ttu-id="97d71-123">Qu’une référence à System. Windows. Forms. dll et System. Core. dll soit ajoutée au projet.</span><span class="sxs-lookup"><span data-stu-id="97d71-123">That a reference to System.Windows.Forms.dll and System.Core.dll be added to the project.</span></span>

- <span data-ttu-id="97d71-124">Que les espaces de noms suivants soient importés :</span><span class="sxs-lookup"><span data-stu-id="97d71-124">That the following namespaces be imported:</span></span>

  [!code-csharp[TimeZone2.Serialization#2](../../../samples/snippets/csharp/VS_Snippets_CLR/TimeZone2.Serialization/cs/SerializeTimeZoneData.cs#2)]
  [!code-vb[TimeZone2.Serialization#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/TimeZone2.Serialization/vb/SerializeTimeZoneData.vb#2)]

## <a name="see-also"></a><span data-ttu-id="97d71-125">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="97d71-125">See also</span></span>

- [<span data-ttu-id="97d71-126">Dates, heures et fuseaux horaires</span><span class="sxs-lookup"><span data-stu-id="97d71-126">Dates, times, and time zones</span></span>](index.md)
- [<span data-ttu-id="97d71-127">Présentation du fuseau horaire</span><span class="sxs-lookup"><span data-stu-id="97d71-127">Time zone overview</span></span>](time-zone-overview.md)
- [<span data-ttu-id="97d71-128">Comment : enregistrer des fuseaux horaires dans une ressource incorporée</span><span class="sxs-lookup"><span data-stu-id="97d71-128">How to: Save time zones to an embedded resource</span></span>](save-time-zones-to-an-embedded-resource.md)
