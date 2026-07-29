# [#](#资源加载器) 资源加载器

`xr-frame`允许开发者定制资源加载器，来添加自己所需的资源类型。所有的资源加载器都需要派生自[AssetLoader](/miniprogram/dev/api/xr-frame/classes/AssetLoader)类，然后使用上一章的方法在`xml`中或者手动使用。

> 在基础库版本**v2.29.2**以上，支持自定义资源加载器。

## [#](#以一个加载器为例) 以一个加载器为例

让我们以内置的纹理加载器为例，

```
import XrFrame from 'XrFrame';
const xrFrameSystem = wx.getXrFrameSystem();

// 指定纹理可接受的额外参数
export interface ITextureLoaderOptions {
  anisoLevel?: number;
}

// 加载纹理时会被传入的数据
type ITextureLoadData = XrFrame.IAssetLoadData<ITextureLoaderOptions>;

// 定制加载器
export default class TextureLoader extends xrFrameSystem.AssetLoader<XrFrame.Texture, ITextureLoaderOptions> {
  // 指定加载器参数的`schema`，和**数据解析**一章中的数据类型一致
  public readonly schema: ILoaderOptionsSchema = {
    anisoLevel: {type: 'number', defaultValue: 1},
  };

  // 当纹理资源加载时会调用这个方法
  public load(
    params: ITextureLoadData,
    callbacks: {
      // 开发者需要在加载进度更新时调用的回调
      onLoading(progress: number): void;
      // 开发者需要在加载完成时调用的回调
      onLoaded(value: Kanata.Texture): void;
      // 开发者需要在加载出错时调用的回调
      onError(error: Error): void;
    }
  ): void {
    const {options} = params;

    // 这里可以拿到当前场景`scene`的引用
    const img = this.scene.createImage();

    img.onload = () => {
      const texture = this.scene.createTexture({
        source: [img],
        width: img.width,
        height: img.height,
        anisoLevel: options.anisoLevel
      });

      callbacks.onLoaded(texture);
    }

    img.onerror = (error) => {
      callbacks.onError(error);
    }

    img.src = params.src;
  }

  // 返回一个当前加载器指定类型资源的**默认资源列表**，这些资源可以直接被组件引用，但它们都是`defer`的，只有在用到的时候才会去加载。
  public getBuiltin() {
    return [
      {
        assetId: 'brdf-lut',
        src: 'https://mmbizwxaminiprogram-1258344707.cos.ap-guangzhou.myqcloud.com/xr-frame/brdflut.png',
        options: {}
      }
    ];
  }

  // 某个资源被取消加载时会调用，记得一定要先调用父级的方法
  public cancel(params: ITextureLoadData) {
    super.cancel();
  }

  // 某个资源被释放时会调用，这里可以执行释放操作
  public release(params: ITextureLoadData, value: XrFrame.Texture) {
    value.destroy();
  }
}

// 注册加载器到框架，资源类型为`texture`
xrFrameSystem.registerAssetLoader('texture', TextureLoader);
```

通过这个纹理加载器我们可以看到，资源系统是通过加载器的`load`、`cancel`、`release`三个方法来管理整个资源的生命周期的。

最后将加载器注册为某种类型后，这种资源类型将会同时被注册进**组件数据解析器**，在`schema`中定义使用。

## [#](#原始加载器) 原始加载器

除了后续会提到的各种类型的资源加载器外，为了最灵活应对需求，框架提供了原始加载器[RawLoader](/miniprogram/dev/api/xr-frame/classes/RawLoader)来加载最原始的数据，其类型为`raw`，`options`为`{encoding: 'binary' | 'utl-8'}`，默认是二进制。

Incorrect translation.