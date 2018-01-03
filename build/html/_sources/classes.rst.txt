.. 
   Static Properties
   Properties
   Public Methods
   Protected Methods
   Static Methods
   Events


.. _classes:

클래스 일람
===========

.. |br| raw:: html

   <br />

.. highlight:: csharp


----------

.. _classes.CameraEffects:

CameraEffects
-------------

카메라 효과와 관련해 여러 스태틱 메소드들을 제공하는 클래스입니다.
`MonoBehaviour`_ 클래스를 상속합니다.


.. _classes.CameraEffects.StaticProperties:

Static Properties
^^^^^^^^^^^^^^^^^

.. _classes.CameraEffects.StaticProperties.Instance:

Instance
""""""""

::

   public static CameraEffects Instance { get; }

:ref:`classes.CameraEffects` 클래스는 싱글턴으로 동작합니다. 인스턴스를 참조하려면 이 프로퍼티를 사용하세요.

----------

.. _classes.CameraEffects.StaticProperties.CurtainImage:

CurtainImage
""""""""""""

::

   public static Image CurtainImage { get; private set; }

페이드 효과에 사용되는 `UI.Image`_\ 입니다. 단순 사용을 위해서는 굳이 변경할 필요 없이 :ref:`classes.CameraEffects.StaticMethods.FadeIn`\ 과 :ref:`classes.CameraEffects.StaticMethods.FadeOut`\ 을 이용해 주세요.

기본 색상은 검정입니다. 색을 하양으로 바꾸고 :ref:`classes.CameraEffects.StaticMethods.FadeIn`\ 을 사용하면 카메라 플래시 효과로도 사용할 수 있습니다.

.. note::
   
   커튼 이미지는 :ref:`uielements.SettingsUI`\ 를 포함한 모든 ToryUX 요소 중 가장 앞에 그려집니다.

----------

.. _classes.CameraEffects.StaticProperties.CurtainCanvasRenderer:

CurtainCanvasRenderer
"""""""""""""""""""""

::

   public static CanvasRenderer CurtainCanvasRenderer { get; }

:ref:`classes.CameraEffects.StaticProperties.CurtainImage`\ 에 달린 `CanvasRenderer`_\ 입니다.
페이드 효과는 내부적으로 이 렌더러의 알파 값을 바꾸는 식으로 구현됩니다.
특별한 일이 없다면 굳이 손 댈 필요는 없습니다.

----------

.. _classes.CameraEffects.StaticProperties.CurtainAlpha:

CurtainAlpha
""""""""""""

::

   public static float CurtainAlpha { get; set; }

:ref:`classes.CameraEffects.StaticProperties.CurtainImage`\ 에 달린 `CanvasRenderer`_\ 의 알파 값입니다.
현재 페이드 효과가 얼마나 진행되었는지 알기 위해, 또는 임의의 효과를 구현하기 위해 접근할 수 있습니다.

----------

.. _classes.CameraEffects.StaticProperties.TranslucentLayer:

TranslucentLayer
""""""""""""""""

::

   public static TranslucentLayer TranslucentLayer { get; }

:ref:`uielements.TitleUI`\ 나 :ref:`uielements.ResultUI` 등에서 UI 외 요소를 블러 처리하는데 사용되는 `TranslucentLayer`_\ 입니다.

----------

.. _classes.CameraEffects.StaticProperties.BloomFlashIntensity:

BloomFlashIntensity
"""""""""""""""""""

::

   public static float BloomFlashIntensity { get; set; } = 5f

:ref:`classes.CameraEffects.StaticMethods.FlashBloom` 효과에 적용될 블룸의 강도입니다.
기본으로 설정한 블룸 값에 이 값이 순간적으로 더해졌다 원래대로 돌아오는 식으로 동작합니다.

----------

.. _classes.CameraEffects.StaticProperties.BloomSettings:

BloomSettings
"""""""""""""

::

   public static BloomModel.Settings BloomSettings { get; set; }

필요할 경우 임의로 `블룸 설정`_\ 을 건드릴 수 있도록 열어 두었습니다.

----------

.. _classes.CameraEffects.StaticProperties.VignetteIntensity:

VignetteIntensity
"""""""""""""""""

::

   public static float VignetteIntensity { get; set; } = 0.45f

:ref:`classes.CameraEffects.StaticMethods.ShowVignetteEffect`\ 에 적용될 비네팅의 강도입니다.
기본으로 설정된 비네팅 값에서 이 값으로 변화하는 식으로 동작합니다.
:ref:`classes.CameraEffects.StaticMethods.HideVignetteEffect`\ 를 호출하면 이 값에서 원래 설정돼있던 비네팅 값으로 변화합니다.

----------

.. _classes.CameraEffects.StaticProperties.VignetteSettings:

VignetteSettings
""""""""""""""""

::

   public static VignetteModel.Settings VignetteSettings { get; set; }

필요할 경우 임의로 `비네팅 설정`_\ 을 건드릴 수 있도록 열어 두었습니다.

----------

.. _classes.CameraEffects.StaticMethods:

Static Methods
^^^^^^^^^^^^^^

.. _classes.CameraEffects.StaticMethods.FadeOut:

FadeOut
"""""""

::

   public static void FadeOut(float duration = 1f, bool ignoreTimeScale = false)

페이드 아웃 효과를 냅니다. :ref:`classes.CameraEffects.StaticProperties.CurtainCanvasRenderer`\ 의 알파 값이 0에서 1로 변화합니다.

:duration:			전환 시간을 설정할 수 있습니다.
:ignoreTimeScale:	게임 시간을 사용할지 실제 시간을 사용할지 설정할 수 있습니다.

----------

.. _classes.CameraEffects.StaticMethods.FadeIn:

FadeIn
""""""

::

   public static void FadeIn(float duration = 1f, bool ignoreTimeScale = false)

페이드 인 효과를 냅니다. :ref:`classes.CameraEffects.StaticProperties.CurtainCanvasRenderer`\ 의 알파 값이 1에서 0으로 변화합니다.

:duration:			전환 시간을 설정할 수 있습니다.
:ignoreTimeScale:	게임 시간을 사용할지 실제 시간을 사용할지 설정할 수 있습니다.

----------

.. _classes.CameraEffects.StaticMethods.Fade:

Fade
""""

::

   public static void Fade(float targetAlpha, float duration = 1f, bool ignoreTimeScale = false)

현재 :ref:`classes.CameraEffects.StaticProperties.CurtainCanvasRenderer`\ 의 알파 값에서 특정한 알파 값으로 변화하는 효과를 냅니다.
진행중인 페이드 인/아웃 효과를 도중에 취소하는 데에 유용합니다.

----------

.. _classes.CameraEffects.StaticMethods.ShowTranslucentLayer:

ShowTranslucentLayer
""""""""""""""""""""

::

   public static void ShowTranslucentLayer(float strength = -1f)

메인 카메라를 블러시키는 레이어를 활성화합니다.

:strength:
   블러의 강도를 설정합니다.
   숫자가 클수록 더욱 덩어리집니다.
   음수 값을 건넬 경우 인스펙터 창에서 설정한 값으로(기본 30) 적용됩니다.

----------

.. _classes.CameraEffects.StaticMethods.HideTranslucentLayer:

HideTranslucentLayer
""""""""""""""""""""

::

   public static void HideTranslucentLayer()

메인 카메라를 블러시키는 레이어를 비활성화합니다.

----------

.. _classes.CameraEffects.StaticMethods.FlashBloom:

FlashBloom
""""""""""

::

   public static void FlashBloom(float duration = 1f)

블룸 터뜨리는 효과를 냅니다. 화면 전환에 유용합니다.

:duration:	효과의 지속 시간을 설정할 수 있습니다.

.. note::

   이 효과는 `블룸 설정`_ 중 ``intensity`` 값만 사용합니다.
   세부 컨트롤이 필요하면 :ref:`classes.CameraEffects.StaticProperties.BloomSettings`\ 를 만져 주세요.

----------

.. _classes.CameraEffects.StaticMethods.ShowVignetteEffect:

ShowVignetteEffect
""""""""""""""""""

::

   public static void ShowVignetteEffect(float duration = 0.1f)

비네팅 효과를 냅니다.
:ref:`classes.CameraEffects.StaticProperties.VignetteIntensity` 값을 바꿔 정도를 조절할 수 있습니다.

:duration:	비네팅 효과가 나타나는 시간을 설정할 수 있습니다.

.. note::

   이 효과는 `비네팅 설정`_ 중 ``intensity`` 값만 사용합니다.
   세부 컨트롤이 필요하면 :ref:`classes.CameraEffects.StaticProperties.VignetteSettings`\ 를 만져 주세요.

----------

.. _classes.CameraEffects.StaticMethods.HideVignetteEffect:

HideVignetteEffect
""""""""""""""""""

::

   public static void HideVignetteEffect(float duration = 0.1f)

비네팅 효과를 끕니다.
:ref:`classes.CameraEffects.StaticMethods.ShowVignetteEffect`\ 를 호출하기 전에 사용하던 비네팅 값이 있다면 그 값으로 되돌아갑니다.

:duration:	비네팅 효과가 사라지는 시간을 설정할 수 있습니다.



----------

.. _classes.UIOrientationSetter:

UIOrientationSetter
-------------------

ToryUX의 오리엔테이션과 관련해 몇 가지 편의 기능을 제공하는 스크립트입니다.
`MonoCollection<T>`_ 클래스를 상속합니다.


.. _classes.UIOrientationSetter.StaticProperties:

Static Properties
^^^^^^^^^^^^^^^^^

.. _classes.UIOrientationSetter.StaticProperties.CurrentOrientation:

CurrentOrientation
""""""""""""""""""

::

   public static UIOrientation CurrentOrientation { get; }

현재 ``UIOrientation`` 값을 확인할 수 있습니다.

.. note::

   ::

      public enum UIOrientation
      {
         Unknown,
         Landscape,
         LandscapeUpsideDown,
         PortraitLeft,
         PortraitRight
      }

----------

.. _classes.UIOrientationSetter.StaticProperties.ReferenceResolution:

ReferenceResolution
"""""""""""""""""""

::

   public static Vector2 ReferenceResolution { get; }

:ref:`classes.UIOrientationSetter`\ 의 부모가 가진 `CanvasScaler`_\ 의 ``referenceResolution`` 값을 돌려줍니다.

.. attention::

   씬 안에 :ref:`classes.UIOrientationSetter`\ 가 둘 이상 존재할 경우 (예컨대 :ref:`gettingstarted.starting.canvasbased`\ ) 모든 부모 `CanvasScaler`_\ 의 ``referenceResolution`` 값이 같아야 정상 동작합니다.

   만약 제대로 설정돼 있지 않더라도 아무런 오류를 띄우지 않으니 주의해 주세요.


----------

.. _classes.UIOrientationSetter.Properties:

Properties
^^^^^^^^^^

.. _classes.UIOrientationSetter.Properties.Orientation:

Orientation
"""""""""""

::

   public UIOrientation Orientation { get; set; }

현재 ``UIOrientation`` 값을 읽거나 지정할 수 있습니다.

.. attention::

   이 프로퍼티는 개별 :ref:`classes.UIOrientationSetter` 인스턴스의 값입니다.

   씬 안에 :ref:`classes.UIOrientationSetter`\ 가 둘 이상 존재할 경우 (예컨대 :ref:`gettingstarted.starting.canvasbased`\ ) 이 프로퍼티에 수동으로 값을 넣어도 다른 :ref:`classes.UIOrientationSetter`\ 에는 적용되지 않으므로, :ref:`classes.UIOrientationSetter.StaticMethods.SetOrientation` 스태틱 메소드를 사용해 주세요.


----------

.. _classes.UIOrientationSetter.StaticMethods:

Static Methods
^^^^^^^^^^^^^^

.. _classes.UIOrientationSetter.StaticMethods.SetOrientation:

SetOrientation
""""""""""""""

::

   public static void SetOrientation(UIOrientation newOrientation)

새 ``UIOrientation`` 값으로 설정합니다.
씬 안에 :ref:`classes.UIOrientationSetter`\ 가 둘 이상 존재할 경우 모든 인스턴스에 적용됩니다.

:newOrientation:	새로 사용할 ``UIOrientation`` 값을 지정합니다.

----------

.. _classes.UIOrientationSetter.StaticMethods.FlipOrientation:

FlipOrientation
"""""""""""""""

::

   public static void FlipOrientation()

화면을 뒤집습니다.
씬 안에 :ref:`classes.UIOrientationSetter`\ 가 둘 이상 존재할 경우 모든 인스턴스에 적용됩니다.


.. _`Monobehaviour`: https://docs.unity3d.com/ScriptReference/MonoBehaviour.html
.. _`UI.Image`: https://docs.unity3d.com/ScriptReference/UI.Image.html
.. _`CanvasRenderer`: https://docs.unity3d.com/ScriptReference/CanvasRenderer.html
.. _`TranslucentLayer`: http://tid.readthedocs.io/en/latest/index.html
.. _`블룸 설정`: https://docs.unity3d.com/Manual/PostProcessing-Bloom.html
.. _`비네팅 설정`: https://docs.unity3d.com/Manual/PostProcessing-Vignette.html
.. _`MonoCollection<T>`: https://answers.unity.com/comments/445235/view.html
.. _`CanvasScaler`: https://docs.unity3d.com/ScriptReference/UI.CanvasScaler.html