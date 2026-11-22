# オーディオ差し替えガイド（public/audio/）

このフォルダの音源ファイル（`.mp3` / `.ogg` / `.wav`）は、`public/audio/manifest.json` を通じて自動ロードされる。

## 差し替え・追加方法
1. **既存トラックの差し替え**：同じファイル名（例：`bgm_explore.mp3`, `se_coin.ogg`）でファイルを上書きすれば、コード変更なしでそのまま新音源が鳴る。
2. **別ファイル名・拡張子での変更**：`manifest.json` の該当キーの `file` パスと `volume` / `playbackRate` / `loop` を編集する。
3. **Web Audio シンセへのフォールバック**：`manifest.json` で値を `null` にすると、ネットワーク読み込みを一切行わず、内蔵の Web Audio API シンセ合成音へ自動フォールバックする（例：連続取得の音階上昇を強調したいジングル等）。

## スロット一覧
- **BGM (`bgm`)**：`title`, `explore`, `fever`, `boss`, `victory`
- **SE (`sfx`)**：`jump`, `stomp`, `hipDropStart`, `hipDropSlam`, `coin`, `star`, `trampoline`, `cushion`, `blockHit`, `boxBreak`, `damage`, `feverStart`, `tutorialCheck`, `bossSlam`, `bossHit`, `bossDefeat`, `chestOpen`, `uiClick`
- ※ `coin` と `stomp` は再生時に連続数に応じて C メジャースケール（ドレミファソラシド）で自動ピッチシフトされる。
