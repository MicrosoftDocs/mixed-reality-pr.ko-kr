---
ms.openlocfilehash: 6b9223481ed909961dbb88d03e4b55ef68448525
ms.sourcegitcommit: 13ef9f89ee61fbfe547ecf5fdfdb97560a0de833
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/21/2020
ms.locfileid: "97717328"
---
# <a name="426"></a>[<span data-ttu-id="83266-101">4.26</span><span class="sxs-lookup"><span data-stu-id="83266-101">4.26</span></span>](#tab/426)

### <a name="windows-mixed-reality"></a><span data-ttu-id="83266-102">Windows Mixed Reality</span><span class="sxs-lookup"><span data-stu-id="83266-102">Windows Mixed Reality</span></span>

![제스처 함수 구성에 연결 된 이벤트 begin play의 청사진](../images/unreal-hand-tracking-img-09.png)

<span data-ttu-id="83266-104">그런 다음 코드를 추가 하 여 다음 이벤트를 구독 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="83266-104">Then you should add code to subscribe to the following events:</span></span>

<span data-ttu-id="83266-105">![Windows 공간 입력 보유, 탭 및 왼쪽 조작 제스처의 청사진 ](../images/unreal/key-events.png)
 ![ 세부 정보 패널의 windows 공간 입력 탭 제스처 옵션 스크린샷](../images/unreal/key-events2.png)</span><span class="sxs-lookup"><span data-stu-id="83266-105">![Blueprint of Windows spatial input hold, tap, and left manipulation gestures](../images/unreal/key-events.png)
![Screenshot of Windows spatial input tap gesture options in the details panel](../images/unreal/key-events2.png)</span></span>

### <a name="openxr"></a><span data-ttu-id="83266-106">OpenXR</span><span class="sxs-lookup"><span data-stu-id="83266-106">OpenXR</span></span>

<span data-ttu-id="83266-107">OpenXR에서 제스처 이벤트는 입력 파이프라인을 통해 추적 됩니다.</span><span class="sxs-lookup"><span data-stu-id="83266-107">In OpenXR, gesture events are tracked through the input pipeline.</span></span> <span data-ttu-id="83266-108">직접 상호 작용을 사용 하는 경우 장치에서 탭을 자동으로 인식 하 고 다른 제스처는 선택할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="83266-108">Using hand interaction, the device can automatically recognize Tap and Hold gestures, but not the others.</span></span> <span data-ttu-id="83266-109">이러한 이름을 OpenXRMsftHandInteraction Select 및 그립 매핑 이라고 합니다.</span><span class="sxs-lookup"><span data-stu-id="83266-109">They are named as OpenXRMsftHandInteraction Select and Grip mappings.</span></span> <span data-ttu-id="83266-110">구독을 사용 하도록 설정 하지 않아도 됩니다. 다음과 같이 프로젝트 설정/엔진/입력에서 이벤트를 선언 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="83266-110">You don’t need to enable subscription, you should declare the events in Project Settings/Engine/Input, just like this:</span></span>

![OpenXR 동작 매핑의 스크린샷](../images/unreal-hand-tracking-img-12.png)

# <a name="425"></a>[<span data-ttu-id="83266-112">4.25</span><span class="sxs-lookup"><span data-stu-id="83266-112">4.25</span></span>](#tab/425)

<span data-ttu-id="83266-113">**Windows Mixed Reality 공간 입력** 및 호출 하는 `WindowsMixedRealitySpatialInputFunctionLibrary.h` 코드 파일에를 추가 하 여 c + + 함수에서 청사진 함수를 찾을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="83266-113">You can find the Blueprint function in under **Windows Mixed Reality Spatial Input**, and the C++ function by adding `WindowsMixedRealitySpatialInputFunctionLibrary.h` in your calling code file.</span></span>

![캡처 제스처](../images/unreal/capture-gestures.png)

### <a name="enum"></a><span data-ttu-id="83266-115">열거형</span><span class="sxs-lookup"><span data-stu-id="83266-115">Enum</span></span>
<!-- Deprecated
The `ESPatialInputAxisGestureType` enum describes spatial axis gestures and are [fully documented](../../out-of-scope/deprecated/holograms-211.md).
-->
<span data-ttu-id="83266-116">청사진</span><span class="sxs-lookup"><span data-stu-id="83266-116">Blueprint:</span></span>

![제스처 형식](../images/unreal/gesture-type.png)

<span data-ttu-id="83266-118">C++:</span><span class="sxs-lookup"><span data-stu-id="83266-118">C++:</span></span>
```cpp
enum class ESpatialInputAxisGestureType : uint8
{
    None = 0,
    Manipulation = 1,
    Navigation = 2,
    NavigationRails = 3
};
```

### <a name="function"></a><span data-ttu-id="83266-119">기능</span><span class="sxs-lookup"><span data-stu-id="83266-119">Function</span></span>
<span data-ttu-id="83266-120">함수를 사용 하 여 제스처 캡처를 사용 하거나 사용 하지 않도록 설정할 수 있습니다 `CaptureGestures` .</span><span class="sxs-lookup"><span data-stu-id="83266-120">You can enable and disable gesture capture with the `CaptureGestures` function.</span></span> <span data-ttu-id="83266-121">활성화 된 제스처가 입력 이벤트를 발생 시키면이 함수는 `true` 제스처 캡처가 성공한 경우를 반환 하 고 오류가 발생 하면를 반환 합니다 `false` .</span><span class="sxs-lookup"><span data-stu-id="83266-121">When an enabled gesture fires input events, the function returns `true` if gesture capture succeeded, and `false` if there's an error.</span></span>

<span data-ttu-id="83266-122">청사진</span><span class="sxs-lookup"><span data-stu-id="83266-122">Blueprint:</span></span>

![제스처 BP 캡처](../images/unreal/capture-gestures-bp.png)

<span data-ttu-id="83266-124">C++:</span><span class="sxs-lookup"><span data-stu-id="83266-124">C++:</span></span>
```cpp
static bool UWindowsMixedRealitySpatialInputFunctionLibrary::CaptureGestures(
    bool Tap = false,
    bool Hold = false,
    ESpatialInputAxisGestureType AxisGesture = ESpatialInputAxisGestureType::None,
    bool NavigationAxisX = true,
    bool NavigationAxisY = true,
    bool NavigationAxisZ = true);
```

<span data-ttu-id="83266-125">청사진 및 c + +: 주요 이벤트에서 찾을 수 있는 주요 이벤트는 다음과 같습니다. ![](../images/unreal/key-events.png)</span><span class="sxs-lookup"><span data-stu-id="83266-125">The following are key events, which you can find in Blueprints and C++: ![Key Events](../images/unreal/key-events.png)</span></span>

![주요 이벤트 2](../images/unreal/key-events2.png)
```cpp
const FKey FSpatialInputKeys::TapGesture(TapGestureName);
const FKey FSpatialInputKeys::DoubleTapGesture(DoubleTapGestureName);
const FKey FSpatialInputKeys::HoldGesture(HoldGestureName);

const FKey FSpatialInputKeys::LeftTapGesture(LeftTapGestureName);
const FKey FSpatialInputKeys::LeftDoubleTapGesture(LeftDoubleTapGestureName);
const FKey FSpatialInputKeys::LeftHoldGesture(LeftHoldGestureName);

const FKey FSpatialInputKeys::RightTapGesture(RightTapGestureName);
const FKey FSpatialInputKeys::RightDoubleTapGesture(RightDoubleTapGestureName);
const FKey FSpatialInputKeys::RightHoldGesture(RightHoldGestureName);

const FKey FSpatialInputKeys::LeftManipulationGesture(LeftManipulationGestureName);
const FKey FSpatialInputKeys::LeftManipulationXGesture(LeftManipulationXGestureName);
const FKey FSpatialInputKeys::LeftManipulationYGesture(LeftManipulationYGestureName);
const FKey FSpatialInputKeys::LeftManipulationZGesture(LeftManipulationZGestureName);

const FKey FSpatialInputKeys::LeftNavigationGesture(LeftNavigationGestureName);
const FKey FSpatialInputKeys::LeftNavigationXGesture(LeftNavigationXGestureName);
const FKey FSpatialInputKeys::LeftNavigationYGesture(LeftNavigationYGestureName);
const FKey FSpatialInputKeys::LeftNavigationZGesture(LeftNavigationZGestureName);


const FKey FSpatialInputKeys::RightManipulationGesture(RightManipulationGestureName);
const FKey FSpatialInputKeys::RightManipulationXGesture(RightManipulationXGestureName);
const FKey FSpatialInputKeys::RightManipulationYGesture(RightManipulationYGestureName);
const FKey FSpatialInputKeys::RightManipulationZGesture(RightManipulationZGestureName);

const FKey FSpatialInputKeys::RightNavigationGesture(RightNavigationGestureName);
const FKey FSpatialInputKeys::RightNavigationXGesture(RightNavigationXGestureName);
const FKey FSpatialInputKeys::RightNavigationYGesture(RightNavigationYGestureName);
const FKey FSpatialInputKeys::RightNavigationZGesture(RightNavigationZGestureName);
```

