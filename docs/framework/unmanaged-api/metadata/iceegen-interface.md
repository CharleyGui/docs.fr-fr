---
title: ICeeGen, interface
ms.date: 03/30/2017
api_name:
- ICeeGen
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICeeGen
helpviewer_keywords:
- ICeeGen interface [.NET Framework metadata]
ms.assetid: 383d20b0-efe9-4e71-8fb8-1186b2e7d0c0
topic_type:
- apiref
ms.openlocfilehash: ae3c372951de00b097d0a8437039a3a85bf3aabf
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74426152"
---
# <a name="iceegen-interface"></a>ICeeGen, interface
Fournit des méthodes pour la compilation de code dynamique.  
  
 This interface is obsolete and should not be used.  
  
## <a name="methods"></a>Méthodes  
  
|Méthode|Description|  
|------------|-----------------|  
|[AddSectionReloc, méthode](../../../../docs/framework/unmanaged-api/metadata/iceegen-addsectionreloc-method.md)|Obsolète. Adds a .reloc instruction to the code base.|  
|[AllocateMethodBuffer, méthode](../../../../docs/framework/unmanaged-api/metadata/iceegen-allocatemethodbuffer-method.md)|Obsolète. Creates a buffer of the specified size for a method, and gets the relative virtual address of the method.|  
|[ComputePointer, méthode](../../../../docs/framework/unmanaged-api/metadata/iceegen-computepointer-method.md)|Obsolète. Determines the buffer for the specified code section.|  
|[EmitString, méthode](../../../../docs/framework/unmanaged-api/metadata/iceegen-emitstring-method.md)|Obsolète. Emits the specified string into the code base.|  
|[GenerateCeeFile, méthode](../../../../docs/framework/unmanaged-api/metadata/iceegen-generateceefile-method.md)|Obsolète. Generates a code-base file that contains the code base currently loaded into this `ICeeGen`.|  
|[GenerateCeeMemoryImage, méthode](../../../../docs/framework/unmanaged-api/metadata/iceegen-generateceememoryimage-method.md)|Obsolète. Generates an image in memory for the code base.|  
|[GetIlSection, méthode](../../../../docs/framework/unmanaged-api/metadata/iceegen-getilsection-method.md)|Obsolète. Gets the section of the intermediate language code base referenced by the specified handle.|  
|[GetIMapTokenIface, méthode](../../../../docs/framework/unmanaged-api/metadata/iceegen-getimaptokeniface-method.md)|Obsolète. Gets the interface referenced by the specified token.|  
|[GetMethodBuffer, méthode](../../../../docs/framework/unmanaged-api/metadata/iceegen-getmethodbuffer-method.md)|Obsolète. Gets a buffer of the appropriate size for the method at the specified relative virtual address.|  
|[GetSectionBlock, méthode](../../../../docs/framework/unmanaged-api/metadata/iceegen-getsectionblock-method.md)|Obsolète. Gets a section block of the code base.|  
|[GetSectionCreate, méthode](../../../../docs/framework/unmanaged-api/metadata/iceegen-getsectioncreate-method.md)|Obsolète. Generates and gets a code section using the specified name and flag values.|  
|[GetSectionDataLen, méthode](../../../../docs/framework/unmanaged-api/metadata/iceegen-getsectiondatalen-method.md)|Obsolète. Gets the length of the specified section.|  
|[GetString, méthode](../../../../docs/framework/unmanaged-api/metadata/iceegen-getstring-method.md)|Obsolète. Gets the string stored at the specified relative virtual address.|  
|[GetStringSection, méthode](../../../../docs/framework/unmanaged-api/metadata/iceegen-getstringsection-method.md)|Obsolète. Gets a string representation of the code section referenced by the specified handle.|  
|[TruncateSection, méthode](../../../../docs/framework/unmanaged-api/metadata/iceegen-truncatesection-method.md)|Obsolète. Truncates the specified code section by the specified length.|  
  
## <a name="requirements"></a>spécifications  
 **Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Header:** Cor.h  
  
 **Library:** Used as a resource in MsCorEE.dll  
  
 **Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [Interfaces de métadonnées](../../../../docs/framework/unmanaged-api/metadata/metadata-interfaces.md)
