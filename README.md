<!doctype html>
<html lang="es">
<head>
<meta charset="utf-8"><meta name="viewport" content="width=device-width,initial-scale=1">
<title>TRIBU STUDIO — 0.7</title>
<style>
:root{--bg:#101217;--panel:#191d25;--panel2:#202530;--line:#303746;--text:#eef1f7;--muted:#929bad;--accent:#9582ff;--accent2:#bcb0ff;--green:#65c6a4}
*{box-sizing:border-box}body{margin:0;background:var(--bg);color:var(--text);font:13px/1.4 Inter,system-ui,-apple-system,"Segoe UI",sans-serif}button,input,select{font:inherit}button{cursor:pointer;color:inherit}.app{min-height:100vh;display:flex;flex-direction:column}
.top{height:57px;display:flex;align-items:center;gap:14px;padding:0 16px;background:#171a20;border-bottom:1px solid var(--line);position:sticky;top:0;z-index:8}.brand{font-weight:900;letter-spacing:.13em}.brand span{color:var(--accent2)}.project{color:var(--muted);border-left:1px solid var(--line);padding-left:13px;font-size:11px}.transport{display:flex;align-items:center;gap:6px;margin:auto}.transport button,.topbtn{border:1px solid var(--line);background:var(--panel2);border-radius:8px;padding:7px 10px;min-width:38px}.transport .play{background:var(--accent);border-color:var(--accent);font-weight:800}.transport .play.paused{background:#e0a94a;border-color:#e0a94a;color:#15181e}.transport-time{font:10px/1.2 ui-monospace,monospace;color:#c9d2df;min-width:58px;text-align:center;border:1px solid var(--line);border-radius:7px;padding:7px 6px;background:#11151b}.bpm{font-size:11px;border:1px solid var(--line);border-radius:8px;padding:7px 9px}.topright{display:flex;gap:6px}
.nav{display:flex;gap:5px;padding:8px 14px;background:#15181e;border-bottom:1px solid var(--line);overflow-x:auto}.nav button{white-space:nowrap;border:1px solid transparent;border-radius:8px;padding:8px 11px;background:transparent;color:var(--muted);display:flex;align-items:center;gap:7px}.nav button.active{background:#302b43;border-color:#544a79;color:#e7e1ff}.nav .ico{font-size:16px}
main{width:100%;max-width:1500px;margin:auto;padding:14px 14px 100px}.view{display:none}.view.active{display:block}.viewhead{display:flex;align-items:center;justify-content:space-between;margin:0 0 12px}.viewhead h2{font-size:17px;margin:0}.sub{color:var(--muted);font-size:11px}
.panel{background:var(--panel);border:1px solid var(--line);border-radius:11px;overflow:hidden}.panelhead{padding:10px 12px;border-bottom:1px solid var(--line);display:flex;align-items:center;justify-content:space-between;background:#1c2029}.panelhead strong{font-size:12px}.controls{display:flex;gap:7px;align-items:center;flex-wrap:wrap}.btn{border:1px solid #3a4150;background:#252a35;border-radius:7px;padding:7px 10px;font-size:11px}.btn.primary{background:#51458c;border-color:#7465bf}.btn.on{background:#3a3454;border-color:#8373cf;color:#eee9ff}
select,input[type=number],input[type=text]{background:#202530;color:var(--text);border:1px solid #3a4150;border-radius:7px;padding:7px 8px;font-size:11px}input[type=range]{accent-color:var(--accent);width:100%}
.playlist-shell{overflow:auto;position:relative}.arrangement-playhead{position:absolute;top:0;bottom:0;width:2px;background:#65c6a4;box-shadow:0 0 8px #65c6a4;z-index:6;pointer-events:none;left:145px}.arrangement-playhead:before{content:'';position:absolute;top:0;left:-4px;border-left:5px solid transparent;border-right:5px solid transparent;border-top:7px solid #65c6a4}.timeline{display:grid;grid-template-columns:145px 1fr;min-width:790px;background:#1c2028;border-bottom:1px solid var(--line)}.trackhead{padding:9px 12px;color:var(--muted);font-size:10px;border-right:1px solid var(--line)}.ruler{display:grid;grid-template-columns:repeat(12,minmax(45px,1fr))}.ruler span{padding:8px 5px;border-left:1px solid #424957;color:#aeb5c3;font-size:10px}.trackrow{display:grid;grid-template-columns:145px 1fr;min-width:790px;min-height:64px;border-bottom:1px solid var(--line)}.trackname{display:flex;align-items:center;gap:8px;padding:0 11px;background:#1b1f27;border-right:1px solid var(--line)}.dot{width:9px;height:9px;border-radius:3px}.trackname b{font-size:11px}.trackname small{display:block;color:var(--muted);font-size:9px}.lane{position:relative;display:grid;grid-template-columns:repeat(12,minmax(45px,1fr));background-image:linear-gradient(to right,rgba(255,255,255,.07) 1px,transparent 1px);background-size:calc(100% / 12) 100%;min-height:64px;cursor:crosshair}.clip{position:absolute;top:8px;height:47px;border-radius:6px;padding:5px 7px;overflow:hidden;border:1px solid #ffffff35;cursor:pointer;min-width:20px}.clip b{font-size:10px;white-space:nowrap}.clip small{display:block;font-size:9px;opacity:.8}.pattern{background:linear-gradient(135deg,#a34d3e,#74382f)}.audio{background:linear-gradient(135deg,#438f85,#28675f)}.automation{background:linear-gradient(135deg,#9878d4,#674b9c)}
.piano-wrap{overflow:auto;max-height:65vh}.piano{display:grid;grid-template-columns:52px 1fr;min-width:760px}.keys{background:#171a21;border-right:1px solid var(--line)}.keyrow{height:24px;border-bottom:1px solid #333946;display:flex;align-items:center;justify-content:center;font-size:9px;color:#b7becc}.keyrow.black{background:#252a34;color:#9da5b5}.notearea{position:relative;background:#171b22}.pruler{height:24px;display:grid;grid-template-columns:repeat(16,1fr);background:#202530;border-bottom:1px solid #424957}.pruler span{text-align:center;border-left:1px solid #414958;color:#aab2c1;font-size:9px;padding-top:4px}.notegrid{position:relative;height:288px;background-image:linear-gradient(to right,rgba(255,255,255,.12) 1px,transparent 1px),linear-gradient(to bottom,rgba(255,255,255,.07) 1px,transparent 1px);background-size:calc(100% / 16) 24px,100% 24px;cursor:crosshair;overflow:hidden}.note{position:absolute;height:19px;border-radius:4px;background:#8c78ed;border:1px solid #c2b6ff;box-shadow:inset 0 1px #ffffff30;z-index:2;cursor:grab;touch-action:none}.note.selected{outline:2px solid #fff;z-index:3}.note-label{font-size:8px;padding:2px 4px;color:#fff;pointer-events:none}.velocity{height:90px;border-top:1px solid var(--line);position:relative;background:repeating-linear-gradient(to right,transparent 0 calc(6.25% - 1px),#343b49 calc(6.25% - 1px) 6.25%)}.velbar{position:absolute;bottom:0;width:10px;background:#65b99d;border-radius:3px 3px 0 0}
.piano-playhead{position:absolute;top:0;bottom:0;width:2px;background:#65c6a4;box-shadow:0 0 8px #65c6a4;pointer-events:none;display:none;z-index:5}.piano-playhead.active{display:block}
.gridtools{display:flex;gap:6px;align-items:center;flex-wrap:wrap;padding:9px 11px;background:#1c2028;border-bottom:1px solid var(--line)}
.channels{padding:10px;display:grid;gap:7px}.channel{display:grid;grid-template-columns:120px 1fr 80px;gap:9px;align-items:center;background:#202530;border:1px solid #303746;border-radius:8px;padding:8px}.channelname b{font-size:11px}.steps{display:grid;grid-template-columns:repeat(16,minmax(12px,1fr));gap:3px}.step{height:24px;border:1px solid #414958;border-radius:4px;background:#151920;padding:0;touch-action:manipulation}.step.on{background:#9a83ff;border-color:#c0b4ff;box-shadow:inset 0 1px #fff4}.step.playhead{outline:2px solid #65c6a4;outline-offset:1px;filter:brightness(1.35)}.step:nth-child(4n+1){margin-left:3px}.channel .btn{padding:5px}
.browsergrid{display:grid;grid-template-columns:220px 1fr;min-height:330px}.browser-side{border-right:1px solid var(--line);padding:10px}.browser-side button{display:block;width:100%;text-align:left;background:transparent;border:0;color:#b8bfcd;padding:8px;border-radius:6px;font-size:11px}.browser-side button.active{background:#302b43;color:#eee8ff}.browser-content{padding:14px}.filelist{display:grid;gap:6px}.fileitem{display:flex;justify-content:space-between;align-items:center;padding:9px;background:#202530;border:1px solid #333b49;border-radius:7px;font-size:11px}
.mixer{display:grid;grid-template-columns:repeat(6,minmax(100px,1fr));gap:8px;padding:12px;overflow:auto}.strip{background:#202530;border:1px solid #343b49;border-radius:8px;padding:10px;text-align:center;min-width:90px}.meter{height:90px;width:10px;background:#11151b;border-radius:8px;margin:9px auto;position:relative;overflow:hidden}.meter i{position:absolute;bottom:0;left:0;right:0;height:45%;background:linear-gradient(#e6bd67,#66bd98)}.strip input{writing-mode:vertical-lr;direction:rtl;height:95px;width:22px}.strip b{display:block;font-size:11px}
.synthgrid{display:grid;grid-template-columns:repeat(4,minmax(130px,1fr));gap:10px;padding:12px}.knobcard{background:#202530;border:1px solid #343b49;border-radius:9px;padding:10px}.knobcard label{display:flex;justify-content:space-between;color:#c4cad6;font-size:10px;margin-bottom:7px}.knobcard output{color:var(--accent2)}.keyboard{display:flex;gap:2px;padding:12px;overflow:auto}.key{height:90px;min-width:38px;background:#e9ebef;color:#1b1d22;border:1px solid #999;border-radius:0 0 5px 5px;display:flex;align-items:end;justify-content:center;padding-bottom:7px;font-size:9px}.key.black{background:#303541;color:white;height:58px;min-width:27px;margin:0 -14px;z-index:2;border-color:#111}
.effects{display:grid;grid-template-columns:repeat(3,minmax(170px,1fr));gap:9px;padding:12px}.effect{background:#202530;border:1px solid #343b49;border-radius:9px;padding:10px}.effect h3{font-size:12px;margin:0 0 9px}.effect label{display:flex;justify-content:space-between;color:#b9c1cf;font-size:10px;margin:8px 0 3px}
.bottom{position:fixed;bottom:0;left:0;right:0;background:#171a20f5;backdrop-filter:blur(14px);border-top:1px solid #3a414e;padding:8px 12px calc(8px + env(safe-area-inset-bottom));z-index:9}.dock{max-width:1500px;margin:auto;display:flex;align-items:center;gap:10px}.tools{display:flex;gap:3px;padding:3px;background:#11151b;border:1px solid #303746;border-radius:10px}.tool{min-width:39px;height:40px;border:0;border-radius:7px;background:transparent;color:#aeb6c5;display:flex;flex-direction:column;align-items:center;justify-content:center;gap:1px}.tool.active{background:#39324f;color:#e5deff}.tool i{font-style:normal;font-size:16px}.tool small{font-size:8px}.divider{height:28px;width:1px;background:var(--line)}.cliptypes{display:flex;gap:3px}.cliptypes button{border:1px solid transparent;background:transparent;color:#aeb6c5;border-radius:7px;padding:7px 9px;font-size:10px}.cliptypes button.active{background:#292d38;border-color:#4b4567;color:#f1efff}.spacer{flex:1}.snap{font-size:10px;color:var(--muted);display:flex;gap:6px;align-items:center}.snap select{padding:6px}.more{height:33px;width:34px;border:1px solid #3a4150;background:#202530;border-radius:8px;font-size:18px}
.toast{position:fixed;top:68px;left:50%;transform:translateX(-50%);background:#302b43;border:1px solid #655a94;color:#eee8ff;border-radius:8px;padding:8px 13px;z-index:30;display:none;font-size:11px}
@media(max-width:700px){.top{padding:0 9px}.project,.topright{display:none}.transport{margin-left:auto;margin-right:0;gap:4px}.transport button{padding:6px 8px;min-width:34px}.nav{padding:7px}.nav button{padding:7px 9px;font-size:10px}main{padding:11px 8px 100px}.synthgrid{grid-template-columns:repeat(2,minmax(120px,1fr))}.effects{grid-template-columns:1fr}.browsergrid{grid-template-columns:115px 1fr}.browser-side{padding:5px}.channel{grid-template-columns:75px 1fr}.channel .btn{display:none}.step{height:21px}.dock{gap:6px}.tool{min-width:32px;width:32px}.tool small{font-size:7px}.cliptypes button{padding:6px 6px;font-size:9px}.snap label{display:none}.snap select{max-width:57px}}
@media(max-width:390px){.tool{min-width:29px;width:29px}.tool i{font-size:14px}.tool small{font-size:6px}.cliptypes button{padding:6px 4px}.divider{display:none}.transport button{padding:6px;min-width:30px}}
.note-resize{position:absolute;right:0;top:0;width:9px;height:100%;cursor:ew-resize;background:linear-gradient(90deg,transparent,#ffffff70)}
.mixbuttons{display:flex;justify-content:center;gap:5px;margin:6px 0}
.mixbuttons button{border:1px solid #454d5d;background:#171b22;color:#aeb7c7;border-radius:5px;padding:3px 9px;font-size:10px;font-weight:700}
.mixbuttons button.active{background:#d4a94d;color:#171b22;border-color:#f0ce79}
.strip .pan{width:100%;height:14px;writing-mode:horizontal-tb;direction:ltr;accent-color:#8c78ed}
.strip .meter i{transition:height .06s linear}
.mixer{grid-template-columns:repeat(auto-fit,minmax(170px,1fr));align-items:start}
.strip{min-width:0;display:flex;flex-direction:column;align-items:center;gap:5px}
.strip .route-label{font-size:10px;color:#aeb8c8;margin-top:5px}
.strip .route{width:100%;background:#171c25;color:#e7ebf2;border:1px solid #3b4658;border-radius:6px;padding:7px;font-size:11px}
.strip .channel-fx{width:100%;margin-top:8px;border-top:1px solid #394252;padding-top:8px;text-align:left}
.fx-head{display:flex;align-items:center;justify-content:space-between;gap:5px;margin-bottom:7px}
.fx-head strong{font-size:10px;color:#dbe2ed}
.fx-head button,.fx-slot button{background:#303949;border:1px solid #46536a;color:#e8edf5;border-radius:5px;padding:5px 7px;font-size:10px}
.fx-head button:disabled{opacity:.4}
.fx-slot{background:#171d27;border:1px solid #364153;border-radius:7px;padding:6px;margin:5px 0}
.fx-slot-top{display:flex;gap:4px;align-items:center}
.fx-slot-top select{flex:1;min-width:0;background:#252e3b;color:#f2f4f8;border:1px solid #48556b;border-radius:5px;padding:6px;font-size:10px}
.fx-slot button.active{background:#76553c;border-color:#b98755}
.fx-slot .fx-remove{font-size:15px;line-height:1;padding:4px 7px}
.fx-slot-bottom{display:flex;align-items:center;gap:5px;margin-top:5px;color:#aeb8c8;font-size:9px}
.fx-slot-bottom small{white-space:nowrap}
.fx-slot-bottom input{writing-mode:horizontal-tb!important;direction:ltr!important;height:auto!important;width:100%!important;min-width:30px}
.fx-slot-bottom output{min-width:28px;text-align:right;color:#d9b66b}
@media(max-width:650px){.mixer{grid-template-columns:repeat(2,minmax(145px,1fr));padding:8px}.strip{padding:8px}.strip input:not(.fx-mix){height:75px}.fx-head{flex-wrap:wrap}}
</style></head>
<body>
<div class="app">
<header class="top">
 <div class="brand">TRIBU <span>STUDIO</span></div><div class="project">Untitled Project · <span id="projectView">Playlist</span></div>
 <div class="transport">
   <button id="rewind" title="Ir al inicio">⏮</button>
   <button id="stop" title="Detener">■</button>
   <button class="play" id="play" title="Reproducir / Pausar">▶</button>
   <button id="forward" title="Adelantar">⏭</button>
   <span class="transport-time" id="transportTime">01:01:000</span>
   <span class="bpm">♩ <input id="bpm" type="number" min="40" max="300" value="150" style="width:42px;padding:0;border:0;background:transparent"> BPM</span>
 </div>
 <div class="topright"><button class="topbtn" id="save">⇩ Save</button><button class="topbtn" id="openAudio">＋ Import</button><input type="file" id="audioFile" accept="audio/*" hidden></div>
</header>
<nav class="nav" aria-label="Ventanas principales">
 <button class="active" data-view="playlist"><span class="ico">▦</span> Playlist</button>
 <button data-view="piano"><span class="ico">♬</span> Piano Roll</button>
 <button data-view="channel"><span class="ico">▤</span> Channel Rack</button>
 <button data-view="mixer"><span class="ico">🎚</span> Mixer</button>
 <button data-view="synth"><span class="ico">◉</span> Synth</button>
 <button data-view="effects"><span class="ico">✧</span> Effects</button>
 <button data-view="browser"><span class="ico">▣</span> Browser</button>
</nav>
<main>
<section class="view active" id="view-playlist">
 <div class="viewhead"><h2>Playlist</h2><span class="sub">Arrangement · 4/4 · 12 bars</span></div>
 <div class="panel playlist-shell" id="playlistShell"><div class="timeline"><div class="trackhead">TRACK / LANE</div><div class="ruler" id="ruler"></div></div><div id="tracks"></div></div>
 <div class="sub" style="margin-top:9px">El transporte es contextual: controla la Playlist, el Piano Roll o el Channel Rack según la vista activa.</div>
</section>
<section class="view" id="view-piano">
 <div class="viewhead"><h2>Piano Roll</h2><span class="sub">Dos octavas · Dibuja, mueve, redimensiona y ajusta velocity</span></div>
 <div class="panel">
  <div class="gridtools"><button class="btn primary" id="noteDraw">✎ Draw note</button><button class="btn" id="noteDelete">⌫ Delete</button><label class="sub">Snap <select id="noteSnap"><option value="1">1/16</option><option value="2">1/8</option><option value="4">1/4</option></select></label><button class="btn" id="clearNotes">Clear</button><button class="btn" id="playNotes">▶ Play pattern</button></div>
  <div class="piano-wrap"><div class="piano"><div class="keys" id="keys"></div><div><div class="pruler" id="pruler"></div><div class="notegrid" id="notegrid"><div class="piano-playhead" id="pianoPlayhead"></div></div><div class="velocity" id="velocity"></div></div></div></div>
  <div class="panelhead"><strong>Velocity lane</strong><span class="sub">Selecciona una nota para editar su velocidad</span></div>
 </div>
</section>
<section class="view" id="view-channel">
 <div class="viewhead"><h2>Channel Rack</h2><span class="sub">Secuenciador por pasos · 16 steps</span></div>
 <div class="panel"><div class="panelhead"><strong>Channels</strong><div class="controls"><button class="btn" id="addChannel">＋ Add channel</button><button class="btn primary" id="playDrums">▶ Play pattern</button></div></div><div class="channels" id="channels"></div></div>
</section>
<section class="view" id="view-mixer">
 <div class="viewhead"><h2>Mixer</h2><span class="sub">Faders · Mute/Solo · Panorama · Medidores</span></div>
 <div class="panel"><div class="panelhead"><strong>Channels, inserts & buses</strong><div class="controls"><button class="btn" id="addBus">＋ Add Bus</button><span class="sub">Hasta 10 efectos por canal · Routing</span></div></div><div class="mixer" id="mixer"></div></div>
</section>
<section class="view" id="view-synth">
 <div class="viewhead"><h2>TRIBU SYNTH</h2><span class="sub">Sintetizador polifónico Web Audio · sonido real</span></div>
 <div class="panel"><div class="panelhead"><strong>Oscillator & envelope</strong><div class="controls"><select id="wave"><option>sawtooth</option><option>square</option><option>triangle</option><option>sine</option></select><button class="btn primary" id="testSynth">▶ Test note</button></div></div>
 <div class="synthgrid">
  <div class="knobcard"><label>Cutoff <output id="cutoffOut">8000 Hz</output></label><input id="cutoff" type="range" min="80" max="16000" value="8000"></div>
  <div class="knobcard"><label>Resonance <output id="resoOut">1.0</output></label><input id="reso" type="range" min=".1" max="18" step=".1" value="1"></div>
  <div class="knobcard"><label>Attack <output id="attackOut">0.01 s</output></label><input id="attack" type="range" min=".005" max="2" step=".005" value=".01"></div>
  <div class="knobcard"><label>Release <output id="releaseOut">0.25 s</output></label><input id="release" type="range" min=".03" max="3" step=".01" value=".25"></div>
  <div class="knobcard"><label>Master <output id="synthVolOut">65%</output></label><input id="synthVol" type="range" min="0" max="100" value="65"></div>
  <div class="knobcard"><label>Detune <output id="detuneOut">0 cents</output></label><input id="detune" type="range" min="-1200" max="1200" value="0"></div>
  <div class="knobcard"><label>Reverb send <output id="revSendOut">15%</output></label><input id="revSend" type="range" min="0" max="100" value="15"></div>
  <div class="knobcard"><label>Delay send <output id="delaySendOut">10%</output></label><input id="delaySend" type="range" min="0" max="100" value="10"></div>
 </div>
 <div class="panelhead"><strong>Playable keyboard</strong><span class="sub">Toca las teclas</span></div><div class="keyboard" id="keyboard"></div>
 </div>
</section>
<section class="view" id="view-effects">
 <div class="viewhead"><h2>Effects Rack</h2><span class="sub">Efectos sencillos aplicados al sintetizador</span></div>
 <div class="panel"><div class="panelhead"><strong>Master effects</strong><span class="sub">Activa y ajusta para escuchar el cambio</span></div><div class="effects">
  <div class="effect"><h3><label><input type="checkbox" id="reverbOn" checked> Reverb</label></h3><label>Mix <output id="reverbMixOut">18%</output></label><input id="reverbMix" type="range" min="0" max="100" value="18"></div>
  <div class="effect"><h3><label><input type="checkbox" id="delayOn"> Delay</label></h3><label>Feedback <output id="feedbackOut">28%</output></label><input id="feedback" type="range" min="0" max="85" value="28"><label>Time <output id="delayTimeOut">280 ms</output></label><input id="delayTime" type="range" min="80" max="900" value="280"></div>
  <div class="effect"><h3><label><input type="checkbox" id="distOn"> Distortion</label></h3><label>Drive <output id="driveOut">20%</output></label><input id="drive" type="range" min="0" max="100" value="20"></div>
 </div></div>
</section>
<section class="view" id="view-browser">
 <div class="viewhead"><h2>Browser</h2><span class="sub">Explora sonidos y archivos locales</span></div>
 <div class="panel browsergrid"><aside class="browser-side"><button class="active" data-folder="packs">▸ Packs</button><button data-folder="instruments">▸ Instruments</button><button data-folder="samples">▸ Samples</button><button data-folder="projects">▸ Projects</button><button data-folder="local">▸ My files</button></aside><div class="browser-content"><div class="panelhead" style="margin:-14px -14px 12px"><strong id="folderTitle">Packs</strong><button class="btn" id="browseLocal">＋ Import file</button></div><div class="filelist" id="filelist"></div><p class="sub">Los archivos importados permanecen disponibles durante esta sesión.</p></div></div>
</section>
</main>
<footer class="bottom" id="bottom"><div class="dock">
 <div class="tools" id="playlistTools"><button class="tool active" data-tool="draw"><i>✎</i><small>Draw</small></button><button class="tool" data-tool="paint"><i>▧</i><small>Paint</small></button><button class="tool" data-tool="select"><i>⌖</i><small>Select</small></button><button class="tool" data-tool="slice"><i>✂</i><small>Slice</small></button><button class="tool" data-tool="delete"><i>⌫</i><small>Delete</small></button></div>
 <div class="divider"></div><div class="cliptypes" id="cliptypes"><button class="active" data-type="pattern">Pattern</button><button data-type="audio">Audio</button><button data-type="automation">Auto</button></div>
 <div class="spacer"></div><div class="snap" id="playlistSnap"><label>Snap</label><select id="snap"><option>1/4</option><option>1/8</option><option selected>1/16</option><option>1/32</option><option>None</option></select></div>
 <button class="more" id="more">⋯</button>
</div></footer>
<div class="toast" id="toast"></div>
<script>
(()=> {
const $=id=>document.getElementById(id);
let audioCtx=null,master=null,filter=null,voiceOut=null,verb=null,verbGain=null,delay=null,delayGain=null,feedback=null,dist=null,distGain=null;
let buses={},analyzers={},panners={},channelRoutes={},channelFX={},fxNodes={},notes=[],selectedNote=null,tool='draw',clipType='pattern',clipId=30,trackData=[],channelData=[];
let arrangementPlayhead=null;

/* ============================================================
   UNIFIED TRANSPORT
   ============================================================ */
const transport = {
  state: 'stopped',       // 'stopped' | 'playing' | 'paused'
  mode: null,             // 'playlist' | 'piano' | 'drum'
  timelineStartAudio: 0,
  pausedElapsed: 0,
  nextEventTime: 0,
  nextStep: 0,
  totalSteps: 0,
  totalDuration: 0,
  schedulerId: null,
  uiId: null,
  endTimerId: null,
};

function toast(s){const t=$('toast');t.textContent=s;t.style.display='block';clearTimeout(toast.timer);toast.timer=setTimeout(()=>t.style.display='none',1900)}

function getBPM(){return Math.max(40,Math.min(300,+$('bpm').value||120))}
function getBeatDur(){return 60/getBPM()}
function getBarDur(){return getBeatDur()*4}
function getStepDur(){return getBeatDur()/4}

function getCurrentMode(){
  const active=document.querySelector('.nav button.active');
  const view=active?.dataset.view;
  if(view==='piano')return 'piano';
  if(view==='channel')return 'drum';
  return 'playlist';
}

function getElapsed(){
  if(transport.state==='playing'&&audioCtx)return Math.max(0,audioCtx.currentTime-transport.timelineStartAudio);
  return transport.pausedElapsed;
}

/* -------- AUDIO GRAPH -------- */
function audio(){
  if(audioCtx){if(audioCtx.state==='suspended')audioCtx.resume();return audioCtx}
  const AC=window.AudioContext||window.webkitAudioContext;
  if(!AC){toast('Web Audio no está disponible');return null}
  audioCtx=new AC();
  master=audioCtx.createGain();master.gain.value=.85;master.connect(audioCtx.destination);
  ['Kick','Bass','Lead','FX','Synth','Bus A','Bus B'].forEach(n=>{
    const g=audioCtx.createGain();g.gain.value=.75;
    const a=audioCtx.createAnalyser();a.fftSize=256;
    const pan=audioCtx.createStereoPanner();pan.pan.value=0;
    buses[n]=g;analyzers[n]=a;panners[n]=pan;channelFX[n]=[];channelRoutes[n]='Master';
  });
  filter=audioCtx.createBiquadFilter();filter.type='lowpass';filter.frequency.value=+$('cutoff').value;filter.Q.value=+$('reso').value;
  voiceOut=audioCtx.createGain();filter.connect(voiceOut);voiceOut.connect(buses.Synth);
  verb=audioCtx.createConvolver();
  const len=Math.floor(audioCtx.sampleRate*1.4),buf=audioCtx.createBuffer(2,len,audioCtx.sampleRate);
  for(let c=0;c<2;c++){const d=buf.getChannelData(c);for(let i=0;i<len;i++)d[i]=(Math.random()*2-1)*Math.pow(1-i/len,2.6)}
  verb.buffer=buf;verbGain=audioCtx.createGain();verbGain.gain.value=0;
  delay=audioCtx.createDelay(1.5);delay.delayTime.value=.28;
  delayGain=audioCtx.createGain();delayGain.gain.value=0;
  feedback=audioCtx.createGain();feedback.gain.value=.25;
  dist=audioCtx.createWaveShaper();dist.oversample='4x';distGain=audioCtx.createGain();distGain.gain.value=0;
  filter.connect(verb);verb.connect(verbGain);verbGain.connect(buses.FX);
  filter.connect(delay);delay.connect(delayGain);delayGain.connect(buses.FX);
  delay.connect(feedback);feedback.connect(delay);
  filter.connect(dist);dist.connect(distGain);distGain.connect(buses.FX);
  rewireAllChannels();updateFX();applyMixer();
  if(!audio._meterStarted){audio._meterStarted=true;meterLoop()}
  return audioCtx;
}
function updateFX(){
  if(!audioCtx)return;
  verbGain.gain.value=$('reverbOn').checked?+$('reverbMix').value/100:0;
  delayGain.gain.value=$('delayOn')?+$('delaySend').value/100:0;
  feedback.gain.value=+$('feedback').value/100;
  delay.delayTime.value=+$('delayTime').value/1000;
  distGain.gain.value=$('distOn').checked?1:0;
  const k=+$('drive').value*4+1,n=2048,curve=new Float32Array(n);
  for(let i=0;i<n;i++){const x=i*2/n-1;curve[i]=(1+k)*x/(1+k*Math.abs(x))}
  dist.curve=curve;
}
function midiHz(m){return 440*Math.pow(2,(m-69)/12)}

function playTone(midi=60,duration=.3,velocity=.8){
  const ctx=audio();if(!ctx)return;
  const now=ctx.currentTime,osc=ctx.createOscillator(),gain=ctx.createGain();
  osc.type=$('wave').value;osc.frequency.setValueAtTime(midiHz(midi),now);osc.detune.value=+$('detune').value;
  const attack=+$('attack').value,release=+$('release').value;
  gain.gain.setValueAtTime(.0001,now);
  gain.gain.linearRampToValueAtTime(Math.max(.0001,velocity*(+$('synthVol').value/100)),now+attack);
  gain.gain.setTargetAtTime(.0001,now+Math.max(attack+.01,duration),Math.max(.015,release/4));
  osc.connect(gain);gain.connect(filter);osc.start(now);osc.stop(now+Math.max(attack+.03,duration)+release*2);
}
function playToneAt(midi,when,duration,velocity){
  const ctx=audio();if(!ctx)return;
  const osc=ctx.createOscillator(),g=ctx.createGain();
  const a=+$('attack').value,r=+$('release').value;
  osc.type=$('wave').value;osc.frequency.value=midiHz(midi);osc.detune.value=+$('detune').value;
  g.gain.setValueAtTime(.0001,when);
  g.gain.linearRampToValueAtTime(Math.max(.0001,velocity*(+$('synthVol').value/100)),when+a);
  g.gain.setTargetAtTime(.0001,when+Math.max(a+.01,duration),Math.max(.015,r/4));
  osc.connect(g);g.connect(filter);osc.start(when);osc.stop(when+duration+r*2);
}

/* -------- DRUM SYNTH -------- */
function drumHit(name,when){
  const ctx=audio();if(!ctx)return;
  const t=Math.max(ctx.currentTime,when??ctx.currentTime);
  const bus=name==='Kick'?buses.Kick:buses.FX;
  const noise=(duration,level,filterType,frequency)=>{
    const len=Math.max(1,Math.floor(ctx.sampleRate*duration)),buf=ctx.createBuffer(1,len,ctx.sampleRate),data=buf.getChannelData(0);
    for(let i=0;i<len;i++)data[i]=Math.random()*2-1;
    const src=ctx.createBufferSource(),g=ctx.createGain(),f=ctx.createBiquadFilter();
    src.buffer=buf;f.type=filterType;f.frequency.setValueAtTime(frequency,t);
    g.gain.setValueAtTime(level,t);g.gain.exponentialRampToValueAtTime(.001,t+duration);
    src.connect(f);f.connect(g);g.connect(bus);src.start(t);src.stop(t+duration);
  };
  if(name==='Kick'){
    const o=ctx.createOscillator(),g=ctx.createGain();
    o.type='sine';o.frequency.setValueAtTime(155,t);o.frequency.exponentialRampToValueAtTime(43,t+.14);
    g.gain.setValueAtTime(.95,t);g.gain.exponentialRampToValueAtTime(.001,t+.32);
    o.connect(g);g.connect(bus);o.start(t);o.stop(t+.33);
  }
  else if(name==='Closed Hat')noise(.055,.20,'highpass',7500);
  else if(name==='Open Hat')noise(.32,.18,'highpass',6200);
  else if(name==='Clap'){noise(.12,.24,'highpass',1200);[.018,.036,.054].forEach(d=>setTimeout(()=>noise(.07,.12,'highpass',1400),d*1000))}
  else if(name==='Snare'){
    noise(.19,.30,'highpass',1500);
    const o=ctx.createOscillator(),g=ctx.createGain();
    o.type='triangle';o.frequency.setValueAtTime(190,t);
    g.gain.setValueAtTime(.22,t);g.gain.exponentialRampToValueAtTime(.001,t+.12);
    o.connect(g);g.connect(bus);o.start(t);o.stop(t+.13);
  }
  else noise(.09,.15,'highpass',1800);
}

/* -------- TRANSPORT CORE -------- */
function clearPlayheads(){
  if(arrangementPlayhead){arrangementPlayhead.remove();arrangementPlayhead=null}
  const ph=$('pianoPlayhead');if(ph)ph.classList.remove('active');
  document.querySelectorAll('.step.playhead').forEach(x=>x.classList.remove('playhead'));
}
function ensureArrangementPlayhead(){
  if(!arrangementPlayhead){
    arrangementPlayhead=document.createElement('div');
    arrangementPlayhead.className='arrangement-playhead';
    $('playlistShell').append(arrangementPlayhead);
  }
}

function scheduleTransport(){
  if(transport.state!=='playing'||!audioCtx)return;
  const ctx=audioCtx,lookAhead=.12,stepDur=getStepDur();
  const loop=transport.mode!=='playlist';
  let guard=0;
  while(transport.nextEventTime<ctx.currentTime+lookAhead&&guard++<64){
    const step=transport.nextStep,when=transport.nextEventTime,localStep=step%16;
    if(transport.mode==='playlist'||transport.mode==='drum'){
      channelData.forEach(c=>{if(c.steps.includes(localStep))drumHit(c.name,when)});
    }
    if(transport.mode==='playlist'||transport.mode==='piano'){
      notes.forEach(n=>{
        if(n.step===localStep){
          const dur=Math.max(.06,(n.len/4)*getBeatDur());
          playToneAt(pitches[n.row],when,dur,n.vel);
        }
      });
    }
    if(loop){
      transport.nextStep=(step+1)%transport.totalSteps;
    } else {
      transport.nextStep=step+1;
      if(transport.nextStep>=transport.totalSteps){
        const endTime=transport.timelineStartAudio+transport.totalSteps*stepDur;
        const delayMs=Math.max(0,(endTime-ctx.currentTime)*1000)+120;
        transport.endTimerId=setTimeout(()=>stopPlayback(),delayMs);
        transport.nextEventTime=Infinity;
        return;
      }
    }
    transport.nextEventTime+=stepDur;
  }
}

function updatePlaylistPlayhead(elapsed){
  ensureArrangementPlayhead();
  const shell=$('playlistShell');if(!shell)return;
  const total=transport.totalDuration||1;
  const pct=Math.min(1,Math.max(0,elapsed/total));
  const contentWidth=Math.max(shell.scrollWidth,shell.clientWidth);
  const laneSpan=Math.max(0,contentWidth-145);
  arrangementPlayhead.style.left=(145+pct*laneSpan)+'px';
}
function updatePianoPlayhead(elapsed){
  const ph=$('pianoPlayhead');if(!ph)return;
  const barDur=getBarDur();
  const pct=(elapsed%barDur)/barDur;
  ph.style.left=(pct*100)+'%';
  ph.classList.add('active');
}
function updateStepHighlights(elapsed){
  const stepDur=getStepDur();
  const step=Math.floor(elapsed/stepDur)%16;
  document.querySelectorAll('.channel').forEach(row=>{
    const cells=row.querySelectorAll('.step');
    cells.forEach((cell,i)=>cell.classList.toggle('playhead',i===step));
  });
}

function updateTransportUI(){
  if(transport.state==='stopped'){$('transportTime').textContent='01:01:000';return}
  const elapsed=getElapsed(),barDur=getBarDur(),beatDur=getBeatDur();
  let bar,inBar;
  if(transport.mode==='playlist'){bar=Math.floor(elapsed/barDur)+1;inBar=elapsed%barDur}
  else{bar=1;inBar=elapsed%barDur}
  const beat=Math.floor(inBar/beatDur)+1;
  const tick=Math.floor(((inBar%beatDur)/beatDur)*960);
  $('transportTime').textContent=String(bar).padStart(2,'0')+':'+String(beat).padStart(2,'0')+':'+String(tick).padStart(3,'0');
  if(transport.mode==='playlist')updatePlaylistPlayhead(elapsed);
  if(transport.mode==='piano')updatePianoPlayhead(elapsed);
  if(transport.mode==='drum'||transport.mode==='playlist')updateStepHighlights(elapsed);
}

function updateTransportButtons(){
  const playBtn=$('play'),notesBtn=$('playNotes'),drumsBtn=$('playDrums');
  const state=transport.state,mode=transport.mode;
  if(state==='playing'){
    playBtn.textContent='Ⅱ';playBtn.classList.add('paused');
    notesBtn.textContent=mode==='piano'?'Ⅱ Pause':'▶ Play pattern';
    drumsBtn.textContent=mode==='drum'?'Ⅱ Pause':'▶ Play pattern';
  } else {
    playBtn.textContent='▶';playBtn.classList.remove('paused');
    notesBtn.textContent='▶ Play pattern';
    drumsBtn.textContent='▶ Play pattern';
  }
  $('bpm').disabled=(state==='playing');
}

function startPlayback(mode){
  const ctx=audio();if(!ctx)return;
  // Toggle pause if same mode & playing
  if(transport.state==='playing'&&transport.mode===mode){pausePlayback();return}
  // Different mode while playing → stop first
  if(transport.state==='playing'&&transport.mode!==mode)stopPlayback();
  // Detect resume
  const resuming=transport.state==='paused'&&transport.mode===mode;
  let elapsed=resuming?transport.pausedElapsed:0;
  // Setup duration / steps
  transport.totalSteps=(mode==='playlist')?192:16;
  transport.totalDuration=transport.totalSteps*getStepDur();
  if(elapsed>=transport.totalDuration)elapsed=0;
  transport.mode=mode;
  transport.state='playing';
  transport.timelineStartAudio=ctx.currentTime-elapsed;
  transport.pausedElapsed=0;
  // Schedule from current position
  const stepDur=getStepDur();
  let nextStep=Math.ceil(elapsed/stepDur);
  if(nextStep>=transport.totalSteps)nextStep=0;
  transport.nextStep=nextStep;
  transport.nextEventTime=transport.timelineStartAudio+nextStep*stepDur;
  // Start loops
  clearInterval(transport.schedulerId);clearInterval(transport.uiId);
  if(transport.endTimerId){clearTimeout(transport.endTimerId);transport.endTimerId=null}
  transport.schedulerId=setInterval(scheduleTransport,25);
  transport.uiId=setInterval(updateTransportUI,30);
  scheduleTransport();
  updateTransportUI();
  updateTransportButtons();
}

function pausePlayback(){
  if(transport.state!=='playing')return;
  transport.pausedElapsed=audioCtx.currentTime-transport.timelineStartAudio;
  transport.state='paused';
  clearInterval(transport.schedulerId);clearInterval(transport.uiId);
  if(transport.endTimerId){clearTimeout(transport.endTimerId);transport.endTimerId=null}
  transport.schedulerId=null;transport.uiId=null;
  updateTransportUI();
  updateTransportButtons();
}

function stopPlayback(){
  transport.state='stopped';
  transport.mode=null;
  transport.pausedElapsed=0;
  transport.timelineStartAudio=0;
  transport.nextStep=0;
  transport.nextEventTime=0;
  transport.totalDuration=0;
  clearInterval(transport.schedulerId);clearInterval(transport.uiId);
  if(transport.endTimerId){clearTimeout(transport.endTimerId);transport.endTimerId=null}
  transport.schedulerId=null;transport.uiId=null;
  clearPlayheads();
  $('transportTime').textContent='01:01:000';
  updateTransportButtons();
}

function rewindTransport(){
  if(transport.state==='playing'){
    transport.timelineStartAudio=audioCtx.currentTime;
    transport.nextStep=0;
    transport.nextEventTime=audioCtx.currentTime;
  } else if(transport.state==='paused'){
    transport.pausedElapsed=0;
  }
  updateTransportUI();
  toast('Inicio');
}

function forwardTransport(){
  const advance=transport.mode==='playlist'?getBarDur():getBeatDur();
  if(transport.state==='playing'){
    const current=audioCtx.currentTime-transport.timelineStartAudio;
    const next=Math.min(transport.totalDuration-.001,current+advance);
    transport.timelineStartAudio=audioCtx.currentTime-next;
    const stepDur=getStepDur();
    let ns=Math.ceil(next/stepDur);
    if(ns>=transport.totalSteps)ns=transport.totalSteps-1;
    transport.nextStep=ns;
    transport.nextEventTime=transport.timelineStartAudio+ns*stepDur;
  } else if(transport.state==='paused'){
    transport.pausedElapsed=Math.min(transport.totalDuration-.001,transport.pausedElapsed+advance);
  }
  updateTransportUI();
  toast(transport.mode==='playlist'?'+1 compás':'+1 tiempo');
}

/* -------- NAVIGATION -------- */
document.querySelectorAll('.nav button').forEach(b=>b.onclick=()=>{
  document.querySelectorAll('.nav button').forEach(x=>x.classList.toggle('active',x===b));
  document.querySelectorAll('.view').forEach(v=>v.classList.toggle('active',v.id==='view-'+b.dataset.view));
  $('projectView').textContent=b.textContent.trim();
  const isPlaylist=b.dataset.view==='playlist';
  $('playlistTools').style.display=isPlaylist?'flex':'none';
  $('cliptypes').style.display=isPlaylist?'flex':'none';
  $('playlistSnap').style.display=isPlaylist?'flex':'none';
  $('bottom').style.display=isPlaylist?'block':'none';
  updateTransportButtons();
});
$('bottom').style.display='block';

/* -------- PLAYLIST -------- */
const names=['Kick','Rumble','Bass','Lead','Atmosphere','FX'],colors=['#b85d49','#a17bd0','#4f9b8f','#c39a4c','#5c83bd','#b56c91'];
for(let i=1;i<=12;i++){const s=document.createElement('span');s.textContent=i;$('ruler').append(s)}
trackData=names.map((name,i)=>({name,color:colors[i],clips:[]}));
function addClip(t,start,len,type,label){t.clips.push({id:clipId++,start,len,type,label})}
addClip(trackData[0],0,2,'pattern','Kick Pattern');addClip(trackData[0],4,2,'pattern','Kick Pattern');addClip(trackData[0],8,2,'pattern','Kick Pattern');
addClip(trackData[1],0,4,'audio','Rumble Layer');addClip(trackData[1],4,4,'audio','Rumble Layer');
addClip(trackData[2],2,3,'pattern','Bassline');addClip(trackData[3],0,3,'pattern','Main Lead');
addClip(trackData[4],0,6,'automation','Filter Cutoff');addClip(trackData[5],9,2,'audio','Riser');

function renderPlaylist(){
  $('tracks').innerHTML='';
  trackData.forEach((t,i)=>{
    const row=document.createElement('div');row.className='trackrow';
    const nm=document.createElement('div');nm.className='trackname';
    nm.innerHTML=`<i class="dot" style="background:${t.color}"></i><div><b>${t.name}</b><small>Track ${String(i+1).padStart(2,'0')}</small></div>`;
    const lane=document.createElement('div');lane.className='lane';
    t.clips.forEach(c=>{
      const e=document.createElement('div');
      e.className='clip '+c.type;
      e.style.left=(c.start/12*100)+'%';e.style.width=(c.len/12*100)+'%';
      e.innerHTML=`<b>${c.label}</b><small>${c.type}</small>`;
      e.onclick=ev=>{
        ev.stopPropagation();
        if(tool==='delete'){t.clips=t.clips.filter(x=>x!==c);renderPlaylist()}
        else if(tool==='slice'&&c.len>1){c.len/=2;addClip(t,c.start+c.len,c.len,c.type,c.label+' 2');renderPlaylist()}
        else toast(c.label+' seleccionado');
      };
      lane.append(e);
    });
    lane.onclick=e=>{
      if(tool==='select'||tool==='delete')return;
      const p=(e.clientX-lane.getBoundingClientRect().left)/lane.clientWidth*12;
      const s=Math.floor(p*4)/4;
      addClip(t,s,clipType==='audio'?2:1,clipType,clipType==='automation'?'Automation':clipType==='audio'?'Audio Clip':'Pattern');
      renderPlaylist();
    };
    row.append(nm,lane);
    $('tracks').append(row);
  });
}
renderPlaylist();
document.querySelectorAll('.tool').forEach(b=>b.onclick=()=>{tool=b.dataset.tool;document.querySelectorAll('.tool').forEach(x=>x.classList.toggle('active',x===b))});
document.querySelectorAll('.cliptypes button').forEach(b=>b.onclick=()=>{clipType=b.dataset.type;document.querySelectorAll('.cliptypes button').forEach(x=>x.classList.toggle('active',x===b))});
$('more').onclick=()=>toast('Más herramientas: cuantizar · duplicar · propiedades');

/* -------- PIANO ROLL -------- */
const pitches=Array.from({length:24},(_,i)=>83-i);
const pitchNames=['B','A#','A','G#','G','F#','F','E','D#','D','C#','C'];
pitches.forEach((p,i)=>{
  const k=document.createElement('div');
  k.className='keyrow '+([1,3,6,8,10].includes(i%12)?'black':'');
  k.textContent=pitchNames[i%12]+(Math.floor(p/12)-1);
  k.style.cursor='pointer';
  k.onclick=()=>playTone(p,.25,.75);
  $('keys').append(k);
});
$('notegrid').style.height=(pitches.length*24)+'px';
for(let i=1;i<=16;i++){const s=document.createElement('span');s.textContent=i;$('pruler').append(s)}

let pianoPointer=null;

function renderNotes(){
  // Remove only notes, keep playhead
  $('notegrid').querySelectorAll(':scope > .note').forEach(el=>el.remove());
  $('velocity').innerHTML='';
  notes.forEach(n=>{
    const e=document.createElement('div');
    e.className='note'+(selectedNote===n.id?' selected':'');
    e.style.left=(n.step/16*100)+'%';
    e.style.width=(n.len/16*100)+'%';
    e.style.top=(n.row*24+2)+'px';
    e.innerHTML='<span class="note-label">'+pitchNames[n.row%12]+'</span><span class="note-resize" title="Cambiar duración"></span>';
    e.onclick=ev=>ev.stopPropagation();
    e.onpointerdown=ev=>{
      ev.stopPropagation();selectedNote=n.id;
      if(tool==='delete'){notes=notes.filter(x=>x.id!==n.id);selectedNote=null;renderNotes();return}
      const rect=$('notegrid').getBoundingClientRect();
      const startX=ev.clientX,oldStep=n.step,oldLen=n.len;
      const resize=ev.target.classList.contains('note-resize');
      pianoPointer={id:ev.pointerId,note:n,resize,startX,oldStep,oldLen,rect};
      try{e.setPointerCapture(ev.pointerId)}catch(_){}
    };
    $('notegrid').append(e);
    const v=document.createElement('div');
    v.className='velbar';
    v.style.left=`calc(${(n.step+n.len/2)/16*100}% - 5px)`;
    v.style.height=(n.vel*82)+'px';
    v.title='Velocity '+Math.round(n.vel*127);
    v.onpointerdown=ev=>{
      ev.stopPropagation();selectedNote=n.id;
      const rect=$('velocity').getBoundingClientRect();
      const set=py=>{n.vel=Math.max(.03,Math.min(1,(rect.bottom-py)/rect.height));renderNotes()};
      set(ev.clientY);
      const move=mv=>set(mv.clientY);
      const up=()=>{window.removeEventListener('pointermove',move);window.removeEventListener('pointerup',up)};
      window.addEventListener('pointermove',move);
      window.addEventListener('pointerup',up,{once:true});
    };
    $('velocity').append(v);
  });
}

function onPianoMove(ev){
  if(!pianoPointer)return;
  const p=pianoPointer;
  const dx=(ev.clientX-p.startX)/p.rect.width*16;
  const snap=+$('noteSnap').value||1;
  if(p.resize){
    p.note.len=Math.max(snap,Math.min(16-p.oldStep,Math.round((p.oldLen+dx)/snap)*snap));
  } else {
    p.note.step=Math.max(0,Math.min(16-p.note.len,Math.round((p.oldStep+dx)/snap)*snap));
    const row=Math.floor((ev.clientY-p.rect.top)/24);
    p.note.row=Math.max(0,Math.min(pitches.length-1,row));
  }
  // Live update position only (avoid full re-render on every move)
  const el=$('notegrid').querySelector('.note.selected');
  if(el){
    el.style.left=(p.note.step/16*100)+'%';
    el.style.width=(p.note.len/16*100)+'%';
    el.style.top=(p.note.row*24+2)+'px';
  }
}
function endPianoPointer(){
  if(!pianoPointer)return;
  pianoPointer=null;
  renderNotes();
}

$('notegrid').addEventListener('pointermove',onPianoMove);
window.addEventListener('pointerup',endPianoPointer);
window.addEventListener('pointercancel',endPianoPointer);
$('notegrid').onclick=e=>{
  if(tool==='delete')return;
  // Ignore if drag just ended
  if(pianoPointer)return;
  const r=$('notegrid').getBoundingClientRect();
  const step=Math.max(0,Math.min(15,Math.floor((e.clientX-r.left)/r.width*16)));
  const row=Math.max(0,Math.min(pitches.length-1,Math.floor((e.clientY-r.top)/24)));
  const snap=+$('noteSnap').value||1;
  const n={id:Date.now()+Math.random(),step:Math.floor(step/snap)*snap,row,len:snap,vel:.8};
  notes.push(n);selectedNote=n.id;renderNotes();playTone(pitches[row],.16,.55);
};
$('clearNotes').onclick=()=>{notes=[];selectedNote=null;renderNotes()};
$('noteDelete').onclick=()=>{notes=notes.filter(n=>n.id!==selectedNote);selectedNote=null;renderNotes()};
$('noteDraw').onclick=()=>{tool='draw';toast('Draw activo: toca la cuadrícula para crear notas')};

renderNotes();

/* -------- CHANNEL RACK -------- */
channelData=[
  {name:'Kick',steps:[0,4,8,12]},
  {name:'Clap',steps:[4,12]},
  {name:'Closed Hat',steps:[0,2,4,6,8,10,12,14]},
  {name:'Open Hat',steps:[7,15]},
  {name:'Snare',steps:[4,12]}
];
function renderChannels(){
  $('channels').innerHTML='';
  channelData.forEach(c=>{
    const row=document.createElement('div');row.className='channel';
    const name=document.createElement('div');name.className='channelname';name.innerHTML=`<b>◉ ${c.name}</b>`;
    const steps=document.createElement('div');steps.className='steps';
    for(let i=0;i<16;i++){
      const b=document.createElement('button');b.className='step'+(c.steps.includes(i)?' on':'');
      b.onclick=()=>{c.steps=c.steps.includes(i)?c.steps.filter(x=>x!==i):[...c.steps,i].sort((a,b)=>a-b);b.classList.toggle('on')};
      steps.append(b);
    }
    const opts=document.createElement('button');opts.className='btn';opts.textContent='⋯';
    row.append(name,steps,opts);
    $('channels').append(row);
  });
}
renderChannels();
$('addChannel').onclick=()=>{channelData.push({name:'New Sampler '+(channelData.length-3),steps:[]});renderChannels()};

/* -------- MIXER -------- */
const mixerNames=['Master','Kick','Bass','Lead','FX','Synth','Bus A','Bus B'];
let mixerState={};

function makeFxNode(type){
  const c=audioCtx;
  const input=c.createGain(),output=c.createGain();
  let node=null,wet=null,extra=[];
  if(type==='EQ'){node=c.createBiquadFilter();node.type='peaking';node.frequency.value=1200;node.Q.value=1;node.gain.value=4;input.connect(node);node.connect(output)}
  else if(type==='Filter'){node=c.createBiquadFilter();node.type='lowpass';node.frequency.value=6500;node.Q.value=.8;input.connect(node);node.connect(output)}
  else if(type==='Distortion'||type==='Saturation'){
    node=c.createWaveShaper();node.oversample='4x';
    const curve=new Float32Array(2048),k=type==='Distortion'?18:5;
    for(let i=0;i<curve.length;i++){const x=i*2/curve.length-1;curve[i]=(1+k)*x/(1+k*Math.abs(x))}
    node.curve=curve;input.connect(node);node.connect(output);
  }
  else if(type==='Delay'){
    node=c.createDelay(1.5);node.delayTime.value=.24;
    wet=c.createGain();wet.gain.value=.22;
    const dry=c.createGain();dry.gain.value=.78;
    const fb=c.createGain();fb.gain.value=.18;
    input.connect(dry);dry.connect(output);
    input.connect(node);node.connect(wet);wet.connect(output);
    node.connect(fb);fb.connect(node);extra=[node,wet,dry,fb];
  }
  else if(type==='Reverb'){
    node=c.createConvolver();
    const len=Math.floor(c.sampleRate*1.1),buf=c.createBuffer(2,len,c.sampleRate);
    for(let ch=0;ch<2;ch++){const d=buf.getChannelData(ch);for(let i=0;i<len;i++)d[i]=(Math.random()*2-1)*Math.pow(1-i/len,2.8)}
    node.buffer=buf;
    wet=c.createGain();wet.gain.value=.28;
    const dry=c.createGain();dry.gain.value=.82;
    input.connect(dry);dry.connect(output);
    input.connect(node);node.connect(wet);wet.connect(output);extra=[node,wet,dry];
  }
  else if(type==='Compressor'||type==='Limiter'){
    node=c.createDynamicsCompressor();
    node.threshold.value=type==='Limiter'?-12:-24;
    node.knee.value=type==='Limiter'?0:18;
    node.ratio.value=type==='Limiter'?20:4;
    node.attack.value=.006;node.release.value=.16;
    input.connect(node);node.connect(output);
  }
  else if(type==='Chorus'||type==='Phaser'){
    node=c.createDelay(.08);node.delayTime.value=type==='Chorus'?.018:.004;
    wet=c.createGain();wet.gain.value=.35;
    const dry=c.createGain();dry.gain.value=.85;
    const lfo=c.createOscillator(),depth=c.createGain();
    lfo.frequency.value=type==='Chorus'?.8:.35;
    depth.gain.value=type==='Chorus'?.006:.002;
    lfo.connect(depth);depth.connect(node.delayTime);lfo.start();
    input.connect(dry);dry.connect(output);
    input.connect(node);node.connect(wet);wet.connect(output);extra=[node,wet,dry,lfo,depth];
  }
  return {type,input,output,nodes:[input,output,node,...extra].filter(Boolean),enabled:true};
}
function clearFxNodes(name){(fxNodes[name]||[]).forEach(f=>f.nodes.forEach(n=>{try{n.disconnect()}catch(e){}}));fxNodes[name]=[]}
function buildChannelChain(name){
  if(!audioCtx||!buses[name])return;
  clearFxNodes(name);
  const chain=channelFX[name]||[],active=chain.filter(x=>x.enabled);
  const first=buses[name];try{first.disconnect()}catch(e){}
  let previous=first;
  active.forEach(slot=>{const fx=makeFxNode(slot.type);fx.output.gain.value=(slot.mix??100)/100;previous.connect(fx.input);previous=fx.output;fxNodes[name].push(fx)});
  previous.connect(analyzers[name]);
}
function buildMasterChain(){
  if(!audioCtx||!master)return;
  clearFxNodes('Master');
  try{master.disconnect()}catch(e){}
  let previous=master;
  (channelFX.Master||[]).filter(x=>x.enabled).forEach(slot=>{const fx=makeFxNode(slot.type);fx.output.gain.value=(slot.mix??100)/100;previous.connect(fx.input);previous=fx.output;fxNodes.Master.push(fx)});
  previous.connect(audioCtx.destination);
}
function rebuildChannelOrMaster(name){if(name==='Master')buildMasterChain();else buildChannelChain(name)}
function wouldCycle(source,target){
  if(target==='Master')return false;
  let at=target;const seen=new Set([source]);
  while(at&&at!=='Master'){if(seen.has(at))return true;seen.add(at);at=channelRoutes[at]||'Master'}
  return false;
}
function rewireAllChannels(){
  if(!audioCtx)return;
  Object.keys(panners).forEach(name=>{try{panners[name].disconnect()}catch(e){}panners[name].connect(master)});
  Object.keys(analyzers).forEach(name=>{try{analyzers[name].disconnect()}catch(e){}analyzers[name].connect(panners[name])});
  Object.keys(buses).forEach(name=>buildChannelChain(name));
  buildMasterChain();
  Object.keys(panners).forEach(name=>{
    const target=channelRoutes[name]||'Master';
    if(target!=='Master'&&buses[target]){try{panners[name].disconnect()}catch(e){}panners[name].connect(buses[target])}
  });
}
function addMixerStrip(name){
  if(mixerState[name])return;
  mixerState[name]={volume:75,mute:false,solo:false,pan:0};
  if(audioCtx){
    const g=audioCtx.createGain(),a=audioCtx.createAnalyser(),pan=audioCtx.createStereoPanner();
    a.fftSize=256;
    buses[name]=g;analyzers[name]=a;panners[name]=pan;
    channelFX[name]=[];channelRoutes[name]='Master';
    rewireAllChannels();
  }
  renderMixer();
}
function renderMixer(){
  $('mixer').innerHTML='';
  mixerNames.forEach((n,i)=>{
    const isMaster=n==='Master';
    const d=document.createElement('div');d.className='strip';d.dataset.channel=n;
    d.innerHTML=`<b>${n}</b><div class="meter"><i></i></div>
      <div class="mixbuttons"><button class="mixmute">${isMaster?'—':'M'}</button><button class="mixsolo">${isMaster?'OUT':'S'}</button></div>
      <input aria-label="${n} volume" type="range" min="0" max="100" value="${mixerState[n].volume}" data-mix="${n}">
      <div class="sub"><output>${mixerState[n].volume}%</output> Vol</div>
      ${isMaster?'':`<input class="pan" aria-label="${n} pan" type="range" min="-100" max="100" value="${mixerState[n].pan}"><div class="sub">Pan</div>
      <label class="route-label">Output / Bus</label>
      <select class="route">${['Master',...mixerNames.filter(x=>x!=='Master'&&x!==n)].map(x=>`<option ${((channelRoutes[n]||'Master')===x)?'selected':''}>${x}</option>`).join('')}</select>`}
      <div class="channel-fx"><div class="fx-head"><strong>Effects · ${channelFX[n].length}/10</strong><button class="add-fx" ${channelFX[n].length>=10?'disabled':''}>＋ Add effect</button></div><div class="fx-slots"></div></div>`;
    $('mixer').append(d);
    const vol=d.querySelector('[data-mix]'),mute=d.querySelector('.mixmute'),solo=d.querySelector('.mixsolo'),pan=d.querySelector('.pan'),route=d.querySelector('.route');
    vol.oninput=()=>{mixerState[n].volume=+vol.value;d.querySelector('output').textContent=vol.value+'%';applyMixer()};
    if(!isMaster){
      mute.onclick=()=>{mixerState[n].mute=!mixerState[n].mute;mute.classList.toggle('active',mixerState[n].mute);applyMixer()};
      solo.onclick=()=>{mixerState[n].solo=!mixerState[n].solo;solo.classList.toggle('active',mixerState[n].solo);applyMixer()};
      pan.oninput=()=>{mixerState[n].pan=+pan.value;applyMixer()};
      route.onchange=()=>{
        const dest=route.value;
        if(wouldCycle(n,dest)){toast('Ese enlace crearía un ciclo');route.value=channelRoutes[n]||'Master';return}
        channelRoutes[n]=dest;
        if(audioCtx)rewireAllChannels();
        toast(n+' → '+dest);
      };
    }
    d.querySelector('.add-fx').onclick=()=>{
      if(channelFX[n].length>=10)return;
      channelFX[n].push({id:Date.now()+Math.random(),type:'EQ',enabled:true,mix:100});
      renderMixer();
      if(audioCtx)rebuildChannelOrMaster(n);
    };
    renderFxSlots(n,d);
  });
}
function renderFxSlots(name,strip){
  const host=strip.querySelector('.fx-slots');
  channelFX[name].forEach((slot,index)=>{
    const card=document.createElement('div');card.className='fx-slot';
    card.innerHTML=`<div class="fx-slot-top">
      <select class="fx-type">${['EQ','Filter','Distortion','Saturation','Compressor','Limiter','Reverb','Delay','Chorus','Phaser'].map(t=>`<option ${slot.type===t?'selected':''}>${t}</option>`).join('')}</select>
      <button class="fx-bypass ${slot.enabled?'':'active'}">${slot.enabled?'ON':'OFF'}</button>
      <button class="fx-remove" title="Remove effect">×</button></div>
      <div class="fx-slot-bottom"><small>Level</small><input class="fx-mix" type="range" min="0" max="100" value="${slot.mix??100}"><output>${slot.mix??100}%</output></div>`;
    card.querySelector('.fx-type').onchange=e=>{slot.type=e.target.value;if(audioCtx)rebuildChannelOrMaster(name);toast(slot.type+' cargado en '+name)};
    card.querySelector('.fx-bypass').onclick=e=>{slot.enabled=!slot.enabled;e.target.textContent=slot.enabled?'ON':'OFF';e.target.classList.toggle('active',!slot.enabled);if(audioCtx)rebuildChannelOrMaster(name)};
    card.querySelector('.fx-remove').onclick=()=>{channelFX[name].splice(index,1);renderMixer();if(audioCtx)rebuildChannelOrMaster(name)};
    card.querySelector('.fx-mix').oninput=e=>{
      slot.mix=+e.target.value;card.querySelector('output').textContent=slot.mix+'%';
      if(audioCtx){
        const fxIndex=(channelFX[name]||[]).filter(x=>x.enabled).indexOf(slot);
        if(name==='Master'){if(fxIndex>=0&&fxNodes.Master[fxIndex])fxNodes.Master[fxIndex].output.gain.value=slot.mix/100}
        else if(fxIndex>=0&&fxNodes[name]?.[fxIndex])fxNodes[name][fxIndex].output.gain.value=slot.mix/100;
      }
    };
    host.append(card);
  });
}
mixerNames.forEach((n,i)=>{mixerState[n]={volume:n==='Master'?85:75,mute:false,solo:false,pan:0};channelFX[n]=[];channelRoutes[n]='Master';fxNodes[n]=[]});
renderMixer();
$('addBus').onclick=()=>{
  const n='Bus '+String.fromCharCode(65+mixerNames.filter(x=>x.startsWith('Bus ')).length);
  if(mixerNames.includes(n)){toast('Ya existe ese bus');return}
  mixerNames.push(n);addMixerStrip(n);toast(n+' creado');
};
function applyMixer(){
  if(!audioCtx)return;
  const anySolo=mixerNames.some(n=>n!=='Master'&&mixerState[n]?.solo);
  mixerNames.forEach(n=>{
    if(n==='Master')return;
    const st=mixerState[n],g=buses[n];if(!g)return;
    g.gain.setTargetAtTime((st.mute||(anySolo&&!st.solo)?0:st.volume/100),audioCtx.currentTime,.015);
    if(panners[n])panners[n].pan.setTargetAtTime(st.pan/100,audioCtx.currentTime,.015);
  });
  master.gain.setTargetAtTime(mixerState.Master.volume/100,audioCtx.currentTime,.015);
}
function meterLoop(){
  if(!audioCtx)return;
  Object.entries(analyzers).forEach(([n,a])=>{
    const data=new Uint8Array(a.frequencyBinCount);
    a.getByteTimeDomainData(data);
    let rms=Math.sqrt(data.reduce((s,v)=>s+(v-128)**2,0)/data.length)/128;
    const el=document.querySelector(`.strip[data-channel="${n}"] .meter i`);
    if(el)el.style.height=Math.min(100,Math.max(2,rms*220))+'%';
  });
  requestAnimationFrame(meterLoop);
}

/* -------- SYNTH CONTROLS -------- */
const ranges=['cutoff','reso','attack','release','synthVol','detune','revSend','delaySend','reverbMix','feedback','delayTime','drive'];
const formats={cutoff:v=>v+' Hz',reso:v=>(+v).toFixed(1),attack:v=>(+v).toFixed(3)+' s',release:v=>(+v).toFixed(2)+' s',synthVol:v=>v+'%',detune:v=>v+' cents',revSend:v=>v+'%',delaySend:v=>v+'%',reverbMix:v=>v+'%',feedback:v=>v+'%',delayTime:v=>v+' ms',drive:v=>v+'%'};
ranges.forEach(id=>{
  const x=$(id);if(!x)return;
  x.oninput=()=>{
    const out=$(id+'Out');if(out)out.textContent=formats[id](x.value);
    if(audioCtx){
      if(id==='cutoff'&&filter)filter.frequency.setTargetAtTime(+x.value,audioCtx.currentTime,.02);
      if(id==='reso'&&filter)filter.Q.setTargetAtTime(+x.value,audioCtx.currentTime,.02);
    }
    if(['reverbMix','feedback','delayTime','drive','delaySend'].includes(id))updateFX();
  };
});
['reverbOn','delayOn','distOn'].forEach(id=>$(id).onchange=()=>{audio();updateFX()});
$('testSynth').onclick=()=>playTone(48,.6,.9);

const keyNotes=[60,62,64,65,67,69,71,72,74,76,77,79,81];
const keyLabels=['C','D','E','F','G','A','B','C','D','E','F','G','A'];
keyNotes.forEach((m,i)=>{
  const b=document.createElement('button');b.className='key';b.textContent=keyLabels[i];
  b.onpointerdown=()=>playTone(m,.42,.8);
  $('keyboard').append(b);
});
document.addEventListener('keydown',e=>{
  if(e.repeat||['INPUT','SELECT','TEXTAREA'].includes(document.activeElement.tagName)||e.ctrlKey||e.metaKey)return;
  const map={a:60,w:61,s:62,e:63,d:64,f:65,t:66,g:67,y:68,h:69,u:70,j:71,k:72};
  if(map[e.key.toLowerCase()]!==undefined)playTone(map[e.key.toLowerCase()],.28,.75);
});

/* -------- FILE / IMPORT / SAVE -------- */
$('openAudio').onclick=()=>$('audioFile').click();
$('browseLocal').onclick=()=>$('audioFile').click();
$('audioFile').onchange=e=>{
  const f=e.target.files[0];if(!f)return;
  const item=document.createElement('div');item.className='fileitem';
  item.innerHTML=`<span>♫ ${f.name}</span><span>${(f.size/1048576).toFixed(2)} MB</span>`;
  $('filelist').prepend(item);toast('Archivo añadido al Browser');
};
document.querySelectorAll('[data-folder]').forEach(b=>b.onclick=()=>{
  document.querySelectorAll('[data-folder]').forEach(x=>x.classList.toggle('active',x===b));
  $('folderTitle').textContent=b.dataset.folder;toast('Carpeta '+b.dataset.folder);
});
$('filelist').innerHTML='<div class="fileitem"><span>▸ TRIBU Drum Kit</span><span class="sub">Pack</span></div><div class="fileitem"><span>▸ Factory Presets</span><span class="sub">Synth</span></div><div class="fileitem"><span>▸ Imported Audio</span><span class="sub">Local</span></div>';

$('save').onclick=()=>{
  const data={version:'0.7',bpm:$('bpm').value,notes,channels:channelData,playlist:trackData,mixer:mixerState,effects:channelFX,routes:channelRoutes};
  const blob=new Blob([JSON.stringify(data,null,2)],{type:'application/json'});
  const a=document.createElement('a');
  a.href=URL.createObjectURL(blob);a.download='tribu-studio-project.json';a.click();
  setTimeout(()=>URL.revokeObjectURL(a.href),1000);
  toast('Proyecto exportado en JSON');
};

/* -------- TRANSPORT BUTTON WIRING -------- */
$('play').onclick=()=>{
  const mode=getCurrentMode();
  if(transport.state==='playing'&&transport.mode===mode)pausePlayback();
  else startPlayback(mode);
};
$('stop').onclick=()=>stopPlayback();
$('rewind').onclick=()=>rewindTransport();
$('forward').onclick=()=>forwardTransport();
$('playNotes').onclick=()=>startPlayback('piano');
$('playDrums').onclick=()=>startPlayback('drum');

})();
</script></body></html>
