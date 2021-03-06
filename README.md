# TextureViewer-Unity

Drawing textures with debug-specified shader in IMGUI's GUI Layout manager on Unity.

This package is using [Gist2](https://github.com/nobnak/Gist2) package.

## Demo
[![Demo](http://img.youtube.com/vi/HpbL3llkxhU/mqdefault.jpg)](https://youtu.be/HpbL3llkxhU)

## Example
```csharp
public PIPTextureHolder tex;

protected Rect windowSize = new Rect(10, 10, 10, 10);
protected PIPTextureMaterial mat;

private void OnEnable() {
    mat = new PIPTextureMaterial();
}
private void OnDisable() {
    mat?.Dispose();
    mat = null;
}
private void OnGUI() {
    windowSize = GUILayout.Window(GetInstanceID(), windowSize, Window, name);
}

protected void Window(int id) { 
    using (new GUILayout.VerticalScope()) {
        GUILayout.Label(tex.name);
        tex.DrawTexture(texWidth, texHeight, mat);
    }
    GUI.DragWindow();
}

```
