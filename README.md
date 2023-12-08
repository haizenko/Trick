<?php

use Jaeger\Tag\StringTag;
use Jaeger\Tracer\TracerInterface;

/** @var TracerInterface $tracer */

$span = $tracer->start('Parent Operation Name', [new StringTag('test.tag', 'Hello world in parent')]);
$childSpan = $tracer->start('Child Operation Name', [new StringTag('test.tag', 'Hello world in child')]);
$tracer->finish($childSpan);
$tracer->finish($span);  # Trick
