---
title: 'Procédure : enregistrer des fuseaux horaires dans une ressource incorporée'
ms.date: 04/10/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- time zones [.NET Framework], saving
- time zone objects [.NET Framework], serializing
- time zone objects [.NET Framework], saving
ms.assetid: 3c96d83a-a057-4496-abb0-8f4b12712558
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 9ca39d989cc7bc16ec2678ba5fa53710899f3ac4
ms.sourcegitcommit: 6f28b709592503d27077b16fff2e2eacca569992
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/28/2019
ms.locfileid: "70107159"
---
# <a name="how-to-save-time-zones-to-an-embedded-resource"></a><span data-ttu-id="8e85a-102">Procédure : enregistrer des fuseaux horaires dans une ressource incorporée</span><span class="sxs-lookup"><span data-stu-id="8e85a-102">How to: Save time zones to an embedded resource</span></span>

<span data-ttu-id="8e85a-103">Une application prenant en charge les fuseaux horaires requiert souvent la présence d’un fuseau horaire particulier.</span><span class="sxs-lookup"><span data-stu-id="8e85a-103">A time zone-aware application often requires the presence of a particular time zone.</span></span> <span data-ttu-id="8e85a-104">Toutefois, étant donné que la disponibilité <xref:System.TimeZoneInfo> d’objets individuels dépend des informations stockées dans le Registre du système local, les fuseaux horaires habituellement disponibles peuvent être absents.</span><span class="sxs-lookup"><span data-stu-id="8e85a-104">However, because the availability of individual <xref:System.TimeZoneInfo> objects depends on information stored in the local system's registry, even customarily available time zones may be absent.</span></span> <span data-ttu-id="8e85a-105">En outre, les informations sur les fuseaux horaires personnalisés instanciées <xref:System.TimeZoneInfo.CreateCustomTimeZone%2A> à l’aide de la méthode ne sont pas stockées avec d’autres informations de fuseau horaire dans le registre.</span><span class="sxs-lookup"><span data-stu-id="8e85a-105">In addition, information about custom time zones instantiated by using the <xref:System.TimeZoneInfo.CreateCustomTimeZone%2A> method is not stored with other time zone information in the registry.</span></span> <span data-ttu-id="8e85a-106">Pour vous assurer que ces fuseaux horaires sont disponibles lorsqu’ils sont nécessaires, vous pouvez les enregistrer en les sérialisant et les restaurer ultérieurement en les désérialisant.</span><span class="sxs-lookup"><span data-stu-id="8e85a-106">To ensure that these time zones are available when they are needed, you can save them by serializing them, and later restore them by deserializing them.</span></span>

<span data-ttu-id="8e85a-107">En général, la sérialisation <xref:System.TimeZoneInfo> d’un objet se produit en dehors de l’application prenant en charge les fuseaux horaires.</span><span class="sxs-lookup"><span data-stu-id="8e85a-107">Typically, serializing a <xref:System.TimeZoneInfo> object occurs apart from the time zone-aware application.</span></span> <span data-ttu-id="8e85a-108">Selon le magasin de données utilisé pour stocker les <xref:System.TimeZoneInfo> objets sérialisés, les données de fuseau horaire peuvent être sérialisées dans le cadre d’une routine d’installation ou d’installation (par exemple, lorsque les données sont stockées dans une clé d’application du registre) ou dans le cadre d’une routine utilitaire qui s’exécute avant la compilation de l’application finale (par exemple, lorsque les données sérialisées sont stockées dans un fichier de ressources XML .NET (. resx)).</span><span class="sxs-lookup"><span data-stu-id="8e85a-108">Depending on the data store used to hold serialized <xref:System.TimeZoneInfo> objects, time zone data may be serialized as part of a setup or installation routine (for example, when the data is stored in an application key of the registry), or as part of a utility routine that runs before the final application is compiled (for example, when the serialized data is stored in a .NET XML resource (.resx) file).</span></span>

<span data-ttu-id="8e85a-109">En plus d’un fichier de ressources compilé avec l’application, plusieurs autres magasins de données peuvent être utilisés pour les informations de fuseau horaire.</span><span class="sxs-lookup"><span data-stu-id="8e85a-109">In addition to a resource file that is compiled with the application, several other data stores can be used for time zone information.</span></span> <span data-ttu-id="8e85a-110">Notamment :</span><span class="sxs-lookup"><span data-stu-id="8e85a-110">These include the following:</span></span>

- <span data-ttu-id="8e85a-111">Registre.</span><span class="sxs-lookup"><span data-stu-id="8e85a-111">The registry.</span></span> <span data-ttu-id="8e85a-112">Notez qu’une application doit utiliser les sous-clés de sa propre clé d’application pour stocker des données de fuseau horaire personnalisées plutôt que d’utiliser les sous-clés de HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows NT\CurrentVersion\Time zones.</span><span class="sxs-lookup"><span data-stu-id="8e85a-112">Note that an application should use the subkeys of its own application key to store custom time zone data rather than using the subkeys of HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows NT\CurrentVersion\Time Zones.</span></span>

- <span data-ttu-id="8e85a-113">Fichiers de configuration.</span><span class="sxs-lookup"><span data-stu-id="8e85a-113">Configuration files.</span></span>

- <span data-ttu-id="8e85a-114">Autres fichiers système.</span><span class="sxs-lookup"><span data-stu-id="8e85a-114">Other system files.</span></span>

### <a name="to-save-a-time-zone-by-serializing-it-to-a-resx-file"></a><span data-ttu-id="8e85a-115">Pour enregistrer un fuseau horaire en le sérialisant dans un fichier. resx</span><span class="sxs-lookup"><span data-stu-id="8e85a-115">To save a time zone by serializing it to a .resx file</span></span>

1. <span data-ttu-id="8e85a-116">Récupérez un fuseau horaire existant ou créez un nouveau fuseau horaire.</span><span class="sxs-lookup"><span data-stu-id="8e85a-116">Retrieve an existing time zone or create a new time zone.</span></span>

   <span data-ttu-id="8e85a-117">Pour récupérer un fuseau horaire existant, consultez [procédure: Accédez aux objets UTC et aux objets](../../../docs/standard/datetime/access-utc-and-local.md) de fuseau horaire local prédéfinis et [Comment: Instanciez un objet](../../../docs/standard/datetime/instantiate-time-zone-info.md)TimeZoneInfo.</span><span class="sxs-lookup"><span data-stu-id="8e85a-117">To retrieve an existing time zone, see [How to: Access the predefined UTC and local time zone objects](../../../docs/standard/datetime/access-utc-and-local.md) and [How to: Instantiate a TimeZoneInfo object](../../../docs/standard/datetime/instantiate-time-zone-info.md).</span></span>

   <span data-ttu-id="8e85a-118">Pour créer un nouveau fuseau horaire, appelez l’une des surcharges de la <xref:System.TimeZoneInfo.CreateCustomTimeZone%2A> méthode.</span><span class="sxs-lookup"><span data-stu-id="8e85a-118">To create a new time zone, call one of the overloads of the <xref:System.TimeZoneInfo.CreateCustomTimeZone%2A> method.</span></span> <span data-ttu-id="8e85a-119">Pour plus d’informations, consultez [Guide pratique pour Créer des fuseaux horaires sans](../../../docs/standard/datetime/create-time-zones-without-adjustment-rules.md) règles [d’ajustement et procédure: Créer des fuseaux horaires avec](../../../docs/standard/datetime/create-time-zones-with-adjustment-rules.md)des règles d’ajustement.</span><span class="sxs-lookup"><span data-stu-id="8e85a-119">For more information, see [How to: Create time zones without adjustment rules](../../../docs/standard/datetime/create-time-zones-without-adjustment-rules.md) and [How to: Create time zones with adjustment rules](../../../docs/standard/datetime/create-time-zones-with-adjustment-rules.md).</span></span>

2. <span data-ttu-id="8e85a-120">Appelez la <xref:System.TimeZoneInfo.ToSerializedString%2A> méthode pour créer une chaîne qui contient les données du fuseau horaire.</span><span class="sxs-lookup"><span data-stu-id="8e85a-120">Call the <xref:System.TimeZoneInfo.ToSerializedString%2A> method to create a string that contains the time zone's data.</span></span>

3. <span data-ttu-id="8e85a-121">Instanciez <xref:System.IO.StreamWriter> un objet en fournissant le nom et éventuellement le chemin d’accès du fichier. resx <xref:System.IO.StreamWriter> au constructeur de classe.</span><span class="sxs-lookup"><span data-stu-id="8e85a-121">Instantiate a <xref:System.IO.StreamWriter> object by providing the name and optionally the path of the .resx file to the <xref:System.IO.StreamWriter> class constructor.</span></span>

4. <span data-ttu-id="8e85a-122">Instanciez <xref:System.Resources.ResXResourceWriter> un objet en passant <xref:System.IO.StreamWriter> l’objet au <xref:System.Resources.ResXResourceWriter> constructeur de classe.</span><span class="sxs-lookup"><span data-stu-id="8e85a-122">Instantiate a <xref:System.Resources.ResXResourceWriter> object by passing the <xref:System.IO.StreamWriter> object to the <xref:System.Resources.ResXResourceWriter> class constructor.</span></span>

5. <span data-ttu-id="8e85a-123">Transmettez la chaîne sérialisée du fuseau horaire à <xref:System.Resources.ResXResourceWriter.AddResource%2A?displayProperty=nameWithType> la méthode.</span><span class="sxs-lookup"><span data-stu-id="8e85a-123">Pass the time zone's serialized string to the <xref:System.Resources.ResXResourceWriter.AddResource%2A?displayProperty=nameWithType> method.</span></span>

6. <span data-ttu-id="8e85a-124">Appelez la méthode <xref:System.Resources.ResXResourceWriter.Generate%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="8e85a-124">Call the <xref:System.Resources.ResXResourceWriter.Generate%2A?displayProperty=nameWithType> method.</span></span>

7. <span data-ttu-id="8e85a-125">Appelez la méthode <xref:System.Resources.ResXResourceWriter.Close%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="8e85a-125">Call the <xref:System.Resources.ResXResourceWriter.Close%2A?displayProperty=nameWithType> method.</span></span>

8. <span data-ttu-id="8e85a-126">Fermez l' <xref:System.IO.StreamWriter> objet en appelant sa <xref:System.IO.StreamWriter.Close%2A> méthode.</span><span class="sxs-lookup"><span data-stu-id="8e85a-126">Close the <xref:System.IO.StreamWriter> object by calling its <xref:System.IO.StreamWriter.Close%2A> method.</span></span>

9. <span data-ttu-id="8e85a-127">Ajoutez le fichier. resx généré au projet Visual Studio de l’application.</span><span class="sxs-lookup"><span data-stu-id="8e85a-127">Add the generated .resx file to the application's Visual Studio project.</span></span>

10. <span data-ttu-id="8e85a-128">À l’aide de la fenêtre **Propriétés** dans Visual Studio, assurez-vous que la propriété **action de génération** du fichier. resx est définie sur **ressource incorporée**.</span><span class="sxs-lookup"><span data-stu-id="8e85a-128">Using the **Properties** window in Visual Studio, make sure that the .resx file's **Build Action** property is set to **Embedded Resource**.</span></span>

## <a name="example"></a><span data-ttu-id="8e85a-129">Exemple</span><span class="sxs-lookup"><span data-stu-id="8e85a-129">Example</span></span>

<span data-ttu-id="8e85a-130">L’exemple suivant sérialise un <xref:System.TimeZoneInfo> objet qui représente l’heure centrale et un <xref:System.TimeZoneInfo> objet qui représente la station de Palmer, en Antarctique, sur un fichier de ressources .net XML nommé SerializedTimeZones. resx.</span><span class="sxs-lookup"><span data-stu-id="8e85a-130">The following example serializes a <xref:System.TimeZoneInfo> object that represents Central Standard Time and a <xref:System.TimeZoneInfo> object that represents the Palmer Station, Antarctica time to a .NET XML resource file that is named SerializedTimeZones.resx.</span></span> <span data-ttu-id="8e85a-131">L’heure standard centrale est généralement définie dans le registre. Palmer station, Antarctique est un fuseau horaire personnalisé.</span><span class="sxs-lookup"><span data-stu-id="8e85a-131">Central Standard Time is typically defined in the registry; Palmer Station, Antarctica is a custom time zone.</span></span>

[!code-csharp[TimeZone2.Serialization#1](../../../samples/snippets/csharp/VS_Snippets_CLR/TimeZone2.Serialization/cs/SerializeTimeZoneData.cs#1)]
[!code-vb[TimeZone2.Serialization#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/TimeZone2.Serialization/vb/SerializeTimeZoneData.vb#1)]

<span data-ttu-id="8e85a-132">Cet exemple sérialise <xref:System.TimeZoneInfo> les objets afin qu’ils soient disponibles dans un fichier de ressources au moment de la compilation.</span><span class="sxs-lookup"><span data-stu-id="8e85a-132">This example serializes <xref:System.TimeZoneInfo> objects so that they are available in a resource file at compile time.</span></span>

<span data-ttu-id="8e85a-133">Étant donné <xref:System.Resources.ResXResourceWriter.Generate%2A?displayProperty=nameWithType> que la méthode ajoute des informations d’en-tête complètes à un fichier de ressources XML .net, elle ne peut pas être utilisée pour ajouter des ressources à un fichier existant.</span><span class="sxs-lookup"><span data-stu-id="8e85a-133">Because the <xref:System.Resources.ResXResourceWriter.Generate%2A?displayProperty=nameWithType> method adds complete header information to a .NET XML resource file, it cannot be used to add resources to an existing file.</span></span> <span data-ttu-id="8e85a-134">L’exemple gère cela en recherchant le fichier SerializedTimeZones. resx et, le cas échéant, en stockant toutes ses ressources autres que les fuseaux horaires sérialisées dans un objet <xref:System.Collections.Generic.Dictionary%602> générique.</span><span class="sxs-lookup"><span data-stu-id="8e85a-134">The example handles this by checking for the SerializedTimeZones.resx file and, if it exists, storing all of its resources other than the two serialized time zones to a generic <xref:System.Collections.Generic.Dictionary%602> object.</span></span> <span data-ttu-id="8e85a-135">Le fichier existant est ensuite supprimé et les ressources existantes sont ajoutées à un nouveau fichier SerializedTimeZones. resx.</span><span class="sxs-lookup"><span data-stu-id="8e85a-135">The existing file is then deleted and the existing resources are added to a new SerializedTimeZones.resx file.</span></span> <span data-ttu-id="8e85a-136">Les données de fuseau horaire sérialisées sont également ajoutées à ce fichier.</span><span class="sxs-lookup"><span data-stu-id="8e85a-136">The serialized time zone data is also added to this file.</span></span>

<span data-ttu-id="8e85a-137">Les champs de clé (ou de **nom**) des ressources ne doivent pas contenir d’espaces incorporés.</span><span class="sxs-lookup"><span data-stu-id="8e85a-137">The key (or **Name**) fields of resources should not contain embedded spaces.</span></span> <span data-ttu-id="8e85a-138">La <xref:System.String.Replace%28System.String%2CSystem.String%29> méthode est appelée pour supprimer tous les espaces incorporés dans les identificateurs de fuseau horaire avant de les assigner au fichier de ressources.</span><span class="sxs-lookup"><span data-stu-id="8e85a-138">The <xref:System.String.Replace%28System.String%2CSystem.String%29> method is called to remove all embedded spaces in the time zone identifiers before they are assigned to the resource file.</span></span>

## <a name="compiling-the-code"></a><span data-ttu-id="8e85a-139">Compilation du code</span><span class="sxs-lookup"><span data-stu-id="8e85a-139">Compiling the code</span></span>

<span data-ttu-id="8e85a-140">Cet exemple nécessite :</span><span class="sxs-lookup"><span data-stu-id="8e85a-140">This example requires:</span></span>

- <span data-ttu-id="8e85a-141">Qu’une référence à System. Windows. Forms. dll et System. Core. dll soit ajoutée au projet.</span><span class="sxs-lookup"><span data-stu-id="8e85a-141">That a reference to System.Windows.Forms.dll and System.Core.dll be added to the project.</span></span>

- <span data-ttu-id="8e85a-142">Que les espaces de noms suivants soient importés:</span><span class="sxs-lookup"><span data-stu-id="8e85a-142">That the following namespaces be imported:</span></span>

  [!code-csharp[TimeZone2.Serialization#2](../../../samples/snippets/csharp/VS_Snippets_CLR/TimeZone2.Serialization/cs/SerializeTimeZoneData.cs#2)]
  [!code-vb[TimeZone2.Serialization#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/TimeZone2.Serialization/vb/SerializeTimeZoneData.vb#2)]

## <a name="see-also"></a><span data-ttu-id="8e85a-143">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="8e85a-143">See also</span></span>

- [<span data-ttu-id="8e85a-144">Dates, heures et fuseaux horaires</span><span class="sxs-lookup"><span data-stu-id="8e85a-144">Dates, times, and time zones</span></span>](../../../docs/standard/datetime/index.md)
- [<span data-ttu-id="8e85a-145">Vue d’ensemble des fuseaux horaires</span><span class="sxs-lookup"><span data-stu-id="8e85a-145">Time zone overview</span></span>](../../../docs/standard/datetime/time-zone-overview.md)
- [<span data-ttu-id="8e85a-146">Guide pratique pour Restaurer des fuseaux horaires à partir d’une ressource incorporée</span><span class="sxs-lookup"><span data-stu-id="8e85a-146">How to: Restore time zones from an embedded resource</span></span>](../../../docs/standard/datetime/restore-time-zones-from-an-embedded-resource.md)
