# polyline_animation_plus

A Flutter package for creating smooth, customizable polyline animations on Google Maps. Ideal for apps in transportation, delivery, logistics, tracking, or any project that needs animated route visualizations.

## 🎥 Demo

![Polyline animation demo](docs/demo.gif)

---

## ✨ Features

- 🎬 **Animated polylines** with progressive drawing effects
- 🔁 **Repeatable** or one‑shot animations
- ⏱️ **Custom duration**, delay, and animation curves
- 🗺️ Works on **Android & iOS** (Google Maps)
- 🧩 Supports **multiple animated polylines** simultaneously
- ⚡ Built using the `google_maps_flutter_platform_interface`

---

## 🚀 Getting Started

Add the package to your `pubspec.yaml`:

```yaml
dependencies:
  polyline_animation_plus: ^1.0.1+1
```

Or if using locally (for development):

```yaml
dependencies:
  polyline_animation_plus:
    path: ../polyline_animation_plus
```

Import it:

```dart
import 'package:polyline_animation_plus/polyline_animation_plus.dart';
```

---

## 📌 Usage Example

Below is a basic example of how to animate a polyline on Google Maps.

```dart
final Set<AnimatedPolyline> polylines = {
  AnimatedPolyline(
    polyline: Polyline(
      polylineId: const PolylineId('front'),
      color: Colors.blue,
      width: 4,
      points: MapAnimationUtils.generateEquidistantPolylineByDuration(
        path: yourCoordinatesList,
        duration: const Duration(seconds: 4),
      ),
    ),
    polylineAnimator: const FadeInProgressiveAnimator(
      repeat: true,
      curve: Curves.linear,
      duration: Duration(seconds: 4),
      delayStart: Duration(seconds: 1),
    ),
  ),
  AnimatedPolyline(
    polyline: Polyline(
      polylineId: const PolylineId('back'),
      color: Colors.grey,
      width: 4,
      points: yourCoordinatesList,
    ),
  ),
};

late MapAnimationController mapAnimationController;

onMapCreated(GoogleMapController controller) {
  mapAnimationController = MapAnimationController(
    mapId: controller.mapId,
    vsync: this,
    polylines: polylines,
  );
}
```

More complete examples can be found in the `/example` folder.

---

## 📚 Additional Information

- Issues and feature requests: **GitHub Issues**
- Contributions are welcome! Submit PRs to improve animations or extend support.
- This package is developed by **ToolRides** for advanced route visualizations in transportation and mobility apps.

---

## 📄 License

MIT License — feel free to use it in commercial and open‑source projects.
