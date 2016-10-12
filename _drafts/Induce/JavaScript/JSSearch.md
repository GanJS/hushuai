title: Search
date: 2016-02-27 18:29:00
description: 
categories:
- JavaScript
tags:
- Search
toc: true
author:
comments:
original:
permalink: 
---

　　**自用笔记：**本文属于自用笔记，不做详解，仅供参考。在此记录自己已理解并开始遵循的前端代码规范。What How Why

<!-- more -->
## 同步instagram图片

>新建页面

```
<form name="f" id="form" action="/s" class="fm" onsubmit="javascript:F.call('ps/sug','pssubmit');">
    <div class="bdsug bdsugbg" style="height: auto; display: none;">
        <ul>
            <li data-key="删除英文怎么写" class="bdsug-overflow">
                删除英文 <b>怎么写</b>
            </li>
            <li data-key="删除英文怎么说" class="bdsug-overflow">
                删除英文 <b>怎么说</b>
            </li>
            <li data-key="删除 英文" class="bdsug-overflow">删除 英文</li>
            <li data-key="英文翻译" class="bdsug-overflow">英文翻译</li>
            <li data-key="取消 英文" class="bdsug-overflow">取消 英文</li>
            <li data-key="卸载英文" class="bdsug-overflow">卸载英文</li>
            <li data-key="删除" class="bdsug-overflow">删除</li>
            <li data-key="删除记忆英文" class="bdsug-overflow">删除记忆英文</li>
            <li data-key="移除英文" class="bdsug-overflow">移除英文</li>
            <li data-key="删除文件英文" class="bdsug-overflow">删除文件英文</li>
        </ul>
    </div>
    <span id="s_kw_wrap" class="bg s_ipt_wr quickdelete-wrap">
        <input type="text" class="s_ipt" name="wd" id="kw" maxlength="100" autocomplete="off">
        <a href="javascript:;" id="quickdelete" title="清空" class="quickdelete" style="top: 0px; right: 0px; display: none;"></a>
    </span>
    <input type="hidden" name="rsv_spt" value="1">
    <input type="hidden" name="rsv_iqid" value="0x816681ee0004ef46">
    <input type="hidden" name="issp" value="1">
    <input type="hidden" name="f" value="8">
    <input type="hidden" name="rsv_bp" value="1">
    <input type="hidden" name="rsv_idx" value="2">
    <input type="hidden" name="ie" value="utf-8">
    <input type="hidden" name="tn" value="baiduhome_pg">
    <span class="btn_wr s_btn_wr bg" id="s_btn_wr">
        <input type="submit" value="百度一下" id="su" class="btn self-btn bg s_btn"></span>
    <span class="tools">
        <span id="mHolder">
            <div id="mCon">
                <span>输入法</span>
            </div>
            <ul id="mMenu">
                <li>
                    <a href="javascript:;" name="ime_hw">手写</a>
                </li>
                <li>
                    <a href="javascript:;" name="ime_py">拼音</a>
                </li>
                <li class="ln"></li>
                <li>
                    <a href="javascript:;" name="ime_cl">关闭</a>
                </li>
            </ul>
        </span>
        <span class="bd_bear_home"></span>
    </span>
    <input type="hidden" name="rsv_enter" value="1">
    <input type="hidden" name="inputT" value="9236">
    <input type="hidden" name="rsv_t" value="8137zLkahzPvnNNDMI86VvvuderjawO2yBVs3et3JjTFY0B1b0ir6GHpPDe8P/HSSUxM">
    <input type="hidden" name="rsv_sug3" value="18">
    <input type="hidden" name="rsv_sug1" value="9">
    <input type="hidden" name="rsv_sug7" value="100">
    <input type="hidden" name="oq" value="删除英文">
    <input type="hidden" name="rsv_pq" value="81d4c3a80004fc74">
</form>
```
