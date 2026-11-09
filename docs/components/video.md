# Video

Development Video renders a native player in both Vue and React. This replaces the published React children-only wrapper and extends Vue's earlier player; check [release status](../reference/release-status.md). The expanded API requires matching development core/framework/design packages until release.

Import Video from the framework package. Pass src, title, poster, controls, autoplay, muted, loop, aspectRatio, variant, overlay, preload, tracks, and fallbackText as needed. src is optional; absent or failed sources show an explicit fallback rather than an inert play button. The React children prop and Vue default slot can supply fallback content.

## Media and access

tracks accepts native text tracks with src, optional kind (captions by default), srcLang, label, and default. Supply WebVTT captions/subtitles appropriate to the media and its language; track URLs must be served correctly, including cross-origin policy when applicable. Captions do not get generated automatically. A text transcript can be supplied by the containing application.

Native controls are enabled by default. overlay adds a labelled play button until playback begins. If its play promise is rejected, feedback appears and native controls remain available. With controls disabled, a retry action is supplied. Pending overlay playback is locked against duplicate requests; replacing the source clears state and ignores stale play results. Autoplay remains subject to browser policy; muted is a separate explicit option.

For example, in a development React application:

```tsx
import { Video } from "@paraxe/react";
export function Trailer() {
  return <Video src="/media/trailer.mp4" poster="/media/poster.jpg"
    title="Film trailer" overlay preload="none"
    tracks={[{ src: "/media/captions-en.vtt", kind: "captions", srcLang: "en", label: "English", default: true }]} />;
}
```

Vue uses the same props, for example `<Video src="/media/trailer.mp4" title="Film trailer" overlay />`. Import Video explicitly from `@paraxe/vue`, supply actual files, and import application design/preset/theme CSS as described in the [installation guide](../guides/install-and-theme.md).

preload defaults to metadata; use none when media should not preload. No source means no video request. Native buffering, seeking, sound, and decoding remain browser responsibilities. Video does not supply streaming entitlement, media hosting, DRM, analytics, or licensing.

## Styling and validation

Variants are default, bordered, and cinematic. Ratios use shared media-aspect tokens. Background and play-control tokens are video-background, video-play-background, video-play-text, and video-play-size; they follow preset surfaces and brand/foreground pairing. Overlay focus uses the shared focus ring.

Both framework renderers are checked via Film01 integration. Client tests exercise playback rejection, media failure and recovery, source changes during pending playback, captions, and unavailable sources. Automated tests do not prove decoding, caption accuracy, keyboard behavior across browsers, or optical balance; actual browser review remains required.

See [Film01](../registry/film-01.md) and [current contracts](../reference/current-contracts.md).
