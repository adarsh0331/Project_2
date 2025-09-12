{"type":"excalidraw/clipboard","workspaceId":"OVdMfzq5oihRTZqdkv7n","elements":[{"modifiedBy":"","modifiedAt":1757701519502,"id":"hm9oDFve7ngqKoMLiKf82","x":-49,"y":6,"version":150,"versionNonce":2028069383,"diagramType":"flowchart-diagram","forceAiMode":false,"code":"title End-to-End CI/CD Pipeline: GitHub to Tomcat Deployment\ndirection right\n\n// Groups and nodes\nSource Code Management [color: blue, icon: github] {\n  Developer Pushes Code [shape: oval, color: lightblue, icon: user]\n  GitHub Repository [icon: github, color: blue]\n\n}\n\nContinuous Integration [color: orange, icon: jenkins] {\n  Jenkins Job Triggered [shape: oval, color: orange, icon: jenkins]\n  Clone Code from GitHub [icon: github, color: orange]\n  Pipeline as Code [icon: file-text, color: orange]\n  Build with Maven [icon: package, color: orange]\n  Package Artifact [icon: archive, color: orange]\n}\n\nContinuous Deployment [color: green, icon: play-circle] {\n  Trigger Ansible Playbook [icon: play, color: green]\n  Ansible Copies Artifact to Tomcat [icon: upload, color: green]\n  Restart Tomcat Server [icon: refresh-cw, color: green]\n}\n\nApplication Live [color: purple, icon: server] {\n  Application Running on Tomcat [shape: oval, color: lightpurple, icon: server]\n  Accessible via EC2 Public IP [icon: globe, color: purple]\n}\n\n// Relationships\nDeveloper Pushes Code > GitHub Repository\nGitHub Repository > Jenkins Job Triggered\nJenkins Job Triggered > Clone Code from GitHub\nClone Code from GitHub > Pipeline as Code\nPipeline as Code > Build with Maven\nBuild with Maven  > Package Artifact\nPackage Artifact > Trigger Ansible Playbook\nTrigger Ansible Playbook > Ansible Copies Artifact to Tomcat\nAnsible Copies Artifact to Tomcat > Restart Tomcat Server\nRestart Tomcat Server > Application Running on Tomcat\nApplication Running on Tomcat > Accessible via EC2 Public IP\n","prompt":"","width":1169,"height":625.3333943684896,"isDeleted":false,"type":"diagram","opacity":100,"angle":0,"roughness":1,"shouldApplyRoughness":true,"groupIds":[],"boundElementIds":null,"lockedGroupId":null,"diagramId":null,"containerId":null,"figureId":null,"fillStyle":"solid","backgroundColor":"transparent","strokeColor":"#d7d9dc","strokeWidth":1,"strokeStyle":"solid","strokeSharpness":"round","isBeingGenerated":false,"isSyntaxMissing":false,"isSyntaxBroken":false,"scale":1,"zIndex":0,"lastEditMode":"code","layoutMode":"incremental"},{"id":"b123690c3856a78d3b912e17a006ecda","strokeColor":"#2866c4","backgroundColor":"rgba(247,249,253, 1)","fillStyle":"solid","strokeWidth":0.75,"strokeStyle":"solid","strokeSharpness":"round","roughness":0,"opacity":100,"elementStyle":1,"colorMode":0,"diagramId":"hm9oDFve7ngqKoMLiKf82","diagramEntityId":"Source Code Management","type":"rectangle","isContainer":true,"diagramRole":"group","sizingMode":"auto","compound":{"type":"parent","containerType":"group","settings":{"color":"blue","colorMode":"pastel","styleMode":"shadow","typeface":"rough"},"children":{"label":"SOURCE CODE MANAGEMENT","icon":{"name":"github"}}},"x":10,"y":21,"width":615,"height":146,"angle":0,"groupIds":[],"lockedGroupId":null,"seed":1848108263,"version":37,"versionNonce":776235911,"isDeleted":false,"boundElementIds":null,"modifiedAt":1757701239181,"zIndex":1,"figureId":null},{"id":"a9b4d2470968af6c987c5d7dcce45ade","type":"oval","containerId":"b123690c3856a78d3b912e17a006ecda","diagramId":"hm9oDFve7ngqKoMLiKf82","diagramEntityId":"Developer Pushes Code","diagramRole":"node","strokeColor":"#242424","backgroundColor":"lightblue","fillStyle":"solid","strokeWidth":0.75,"strokeStyle":"solid","strokeSharpness":"round","roughness":0,"opacity":100,"elementStyle":1,"colorMode":0,"x":47,"y":64,"shapeVersion":"v2","compound":{"type":"parent","containerType":"flow-node","settings":{"shape":"oval","color":"lightblue","colorMode":"pastel","styleMode":"shadow","typeface":"rough"},"children":{"label":"Developer\nPushes Code","icon":{"name":"user"}}},"width":138,"height":82.80000000000001,"angle":0,"groupIds":[],"lockedGroupId":null,"seed":1876533863,"version":5,"versionNonce":1041006023,"isDeleted":false,"boundElementIds":["3a0bee441c8a827836d1f044c65ed0ff"],"modifiedAt":1757701098453,"zIndex":2,"figureId":null},{"id":"fbd877b2637f6acf216574d89daa1d8d","type":"rectangle","containerId":"b123690c3856a78d3b912e17a006ecda","diagramId":"hm9oDFve7ngqKoMLiKf82","diagramEntityId":"GitHub Repository","diagramRole":"node","strokeColor":"#242424","backgroundColor":"#c7dcfc","fillStyle":"solid","strokeWidth":0.75,"strokeStyle":"solid","strokeSharpness":[6,6,6,6],"roughness":0,"opacity":100,"elementStyle":1,"colorMode":0,"x":244,"y":69,"shapeVersion":"v2","compound":{"type":"parent","containerType":"flow-node","settings":{"shape":"rectangle","color":"blue","colorMode":"pastel","styleMode":"shadow","typeface":"rough"},"children":{"label":"GitHub\nRepository","icon":{"name":"github"}}},"width":138,"height":72,"angle":0,"groupIds":[],"lockedGroupId":null,"seed":2046576583,"version":33,"versionNonce":1431856681,"isDeleted":false,"boundElementIds":["3a0bee441c8a827836d1f044c65ed0ff","e16c2e50a829d367688841fa4ffcb2a6"],"modifiedAt":1757701098453,"zIndex":3,"figureId":null},{"id":"5488b92da63aecce6c3a94da9ade9e12","strokeColor":"#c38424","backgroundColor":"rgba(253,251,246, 1)","fillStyle":"solid","strokeWidth":0.75,"strokeStyle":"solid","strokeSharpness":"round","roughness":0,"opacity":100,"elementStyle":1,"colorMode":0,"diagramId":"hm9oDFve7ngqKoMLiKf82","diagramEntityId":"Continuous Integration","type":"rectangle","isContainer":true,"diagramRole":"group","sizingMode":"auto","compound":{"type":"parent","containerType":"group","settings":{"color":"orange","colorMode":"pastel","styleMode":"shadow","typeface":"rough"},"children":{"label":"CONTINUOUS INTEGRATION","icon":{"name":"jenkins"}}},"x":-34,"y":227,"width":1048,"height":146,"angle":0,"groupIds":[],"lockedGroupId":null,"seed":1130601031,"version":50,"versionNonce":1333559465,"isDeleted":false,"boundElementIds":null,"modifiedAt":1757701481842,"zIndex":5,"figureId":null},{"id":"29a4a89457cde6f9b8ae27b172493af0","type":"oval","containerId":"5488b92da63aecce6c3a94da9ade9e12","diagramId":"hm9oDFve7ngqKoMLiKf82","diagramEntityId":"Jenkins Job Triggered","diagramRole":"node","strokeColor":"#242424","backgroundColor":"#f8d8c0","fillStyle":"solid","strokeWidth":0.75,"strokeStyle":"solid","strokeSharpness":"round","roughness":0,"opacity":100,"elementStyle":1,"colorMode":0,"x":3,"y":270,"shapeVersion":"v2","compound":{"type":"parent","containerType":"flow-node","settings":{"shape":"oval","color":"orange","colorMode":"pastel","styleMode":"shadow","typeface":"rough"},"children":{"label":"Jenkins Job\nTriggered","icon":{"name":"jenkins"}}},"width":138,"height":82.80000000000001,"angle":0,"groupIds":[],"lockedGroupId":null,"seed":658212487,"version":17,"versionNonce":1549964873,"isDeleted":false,"boundElementIds":["85f565864fa77778c81a6c5de192e189","e16c2e50a829d367688841fa4ffcb2a6"],"modifiedAt":1757701345111,"zIndex":6,"figureId":null},{"id":"d2d0dfc360ac336a065d5bb6850ceb38","type":"rectangle","containerId":"5488b92da63aecce6c3a94da9ade9e12","diagramId":"hm9oDFve7ngqKoMLiKf82","diagramEntityId":"Clone Code from GitHub","diagramRole":"node","strokeColor":"#242424","backgroundColor":"#f8d8c0","fillStyle":"solid","strokeWidth":0.75,"strokeStyle":"solid","strokeSharpness":[6,6,6,6],"roughness":0,"opacity":100,"elementStyle":1,"colorMode":0,"x":200,"y":275,"shapeVersion":"v2","compound":{"type":"parent","containerType":"flow-node","settings":{"shape":"rectangle","color":"orange","colorMode":"pastel","styleMode":"shadow","typeface":"rough"},"children":{"label":"Clone Code from\nGitHub","icon":{"name":"github"}}},"width":138.99203002929687,"height":72,"angle":0,"groupIds":[],"lockedGroupId":null,"seed":1292574695,"version":17,"versionNonce":1007942537,"isDeleted":false,"boundElementIds":["85f565864fa77778c81a6c5de192e189","980546449d74f196ffaa1e927bed22a1"],"modifiedAt":1757701357132,"zIndex":8,"figureId":null},{"id":"ebc26dd97a60bb8a5a773eea8a561c08","type":"rectangle","containerId":"5488b92da63aecce6c3a94da9ade9e12","diagramId":"hm9oDFve7ngqKoMLiKf82","diagramEntityId":"Build with Maven","diagramRole":"node","strokeColor":"#242424","backgroundColor":"#f8d8c0","fillStyle":"solid","strokeWidth":0.75,"strokeStyle":"solid","strokeSharpness":[6,6,6,6],"roughness":0,"opacity":100,"elementStyle":1,"colorMode":0,"x":596,"y":275,"shapeVersion":"v2","compound":{"type":"parent","containerType":"flow-node","settings":{"shape":"rectangle","color":"orange","colorMode":"pastel","styleMode":"shadow","typeface":"rough"},"children":{"label":"Build with Maven","icon":{"name":"package"}}},"width":138.22975463867186,"height":72,"angle":0,"groupIds":[],"lockedGroupId":null,"seed":1016186535,"version":33,"versionNonce":1445136713,"isDeleted":false,"boundElementIds":["b37b66548fba25e634b8db665e124c3a","066ae7b08320ff91f3c7ceca8b77dfa6"],"modifiedAt":1757701429386,"zIndex":0,"figureId":null},{"id":"d4f4541c982eb493bca916ede0f526ad","type":"rectangle","containerId":"5488b92da63aecce6c3a94da9ade9e12","diagramId":"hm9oDFve7ngqKoMLiKf82","diagramEntityId":"Pipeline as Code","diagramRole":"node","strokeColor":"#242424","backgroundColor":"#f8d8c0","fillStyle":"solid","strokeWidth":0.75,"strokeStyle":"solid","strokeSharpness":[6,6,6,6],"roughness":0,"opacity":100,"elementStyle":1,"colorMode":0,"x":398,"y":275,"shapeVersion":"v2","compound":{"type":"parent","containerType":"flow-node","settings":{"shape":"rectangle","color":"orange","colorMode":"pastel","styleMode":"shadow","typeface":"rough"},"children":{"label":"Pipeline as Code","icon":{"name":"file-text"}}},"width":138.65102630615235,"height":72,"angle":0,"groupIds":[],"lockedGroupId":null,"seed":388805959,"version":18,"versionNonce":1482935239,"isDeleted":false,"boundElementIds":["980546449d74f196ffaa1e927bed22a1","b37b66548fba25e634b8db665e124c3a"],"modifiedAt":1757701429386,"zIndex":11,"figureId":null},{"id":"2fc35d4f44b6df811231ac162514dc9a","type":"rectangle","containerId":"5488b92da63aecce6c3a94da9ade9e12","diagramId":"hm9oDFve7ngqKoMLiKf82","diagramEntityId":"Package Artifact","diagramRole":"node","strokeColor":"#242424","backgroundColor":"#f8d8c0","fillStyle":"solid","strokeWidth":0.75,"strokeStyle":"solid","strokeSharpness":[6,6,6,6],"roughness":0,"opacity":100,"elementStyle":1,"colorMode":0,"x":839,"y":275,"shapeVersion":"v2","compound":{"type":"parent","containerType":"flow-node","settings":{"shape":"rectangle","color":"orange","colorMode":"pastel","styleMode":"shadow","typeface":"rough"},"children":{"label":"Package Artifact","icon":{"name":"archive"}}},"width":138,"height":72,"angle":0,"groupIds":[],"lockedGroupId":null,"seed":2082233703,"version":88,"versionNonce":119077703,"isDeleted":false,"boundElementIds":["21c42561ba1488104c56bbe8210f00e0","066ae7b08320ff91f3c7ceca8b77dfa6"],"modifiedAt":1757701481842,"zIndex":14,"figureId":null},{"id":"7e83ad5eb0c5e2863a38ad36d104ed31","strokeColor":"#30a050","backgroundColor":"rgba(247,253,249, 1)","fillStyle":"solid","strokeWidth":0.75,"strokeStyle":"solid","strokeSharpness":"round","roughness":0,"opacity":100,"elementStyle":1,"colorMode":0,"diagramId":"hm9oDFve7ngqKoMLiKf82","diagramEntityId":"Continuous Deployment","type":"rectangle","isContainer":true,"diagramRole":"group","sizingMode":"auto","compound":{"type":"parent","containerType":"group","settings":{"color":"green","colorMode":"pastel","styleMode":"shadow","typeface":"rough"},"children":{"label":"CONTINUOUS DEPLOYMENT","icon":{"name":"play-circle"}}},"x":15,"y":453,"width":631,"height":151,"angle":0,"groupIds":[],"lockedGroupId":null,"seed":1687604135,"version":25,"versionNonce":333150247,"isDeleted":false,"boundElementIds":null,"modifiedAt":1757701473449,"zIndex":16,"figureId":null},{"id":"06c0bc662a7b253df3d556a1e21d2d1d","type":"rectangle","containerId":"7e83ad5eb0c5e2863a38ad36d104ed31","diagramId":"hm9oDFve7ngqKoMLiKf82","diagramEntityId":"Trigger Ansible Playbook","diagramRole":"node","strokeColor":"#242424","backgroundColor":"#c0f8d0","fillStyle":"solid","strokeWidth":0.75,"strokeStyle":"solid","strokeSharpness":[6,6,6,6],"roughness":0,"opacity":100,"elementStyle":1,"colorMode":0,"x":52,"y":502,"shapeVersion":"v2","compound":{"type":"parent","containerType":"flow-node","settings":{"shape":"rectangle","color":"green","colorMode":"pastel","styleMode":"shadow","typeface":"rough"},"children":{"label":"Trigger Ansible\nPlaybook","icon":{"name":"play"}}},"width":138,"height":72,"angle":0,"groupIds":[],"lockedGroupId":null,"seed":760537799,"version":25,"versionNonce":1138016713,"isDeleted":false,"boundElementIds":["49db2f34b1fccf7b3c2cb2e5244cf13a","21c42561ba1488104c56bbe8210f00e0"],"modifiedAt":1757701473449,"zIndex":1,"figureId":null},{"id":"a25606c0c57377fc96f4f78a77f79866","type":"rectangle","containerId":"7e83ad5eb0c5e2863a38ad36d104ed31","diagramId":"hm9oDFve7ngqKoMLiKf82","diagramEntityId":"Ansible Copies Artifact to Tomcat","diagramRole":"node","strokeColor":"#242424","backgroundColor":"#c0f8d0","fillStyle":"solid","strokeWidth":0.75,"strokeStyle":"solid","strokeSharpness":[6,6,6,6],"roughness":0,"opacity":100,"elementStyle":1,"colorMode":0,"x":249,"y":502,"shapeVersion":"v2","compound":{"type":"parent","containerType":"flow-node","settings":{"shape":"rectangle","color":"green","colorMode":"pastel","styleMode":"shadow","typeface":"rough"},"children":{"label":"Ansible Copies\nArtifact to Tomcat","icon":{"name":"upload"}}},"width":142.52259521484376,"height":72,"angle":0,"groupIds":[],"lockedGroupId":null,"seed":334947367,"version":24,"versionNonce":1498128553,"isDeleted":false,"boundElementIds":["49db2f34b1fccf7b3c2cb2e5244cf13a","1624ae739f06a4cdaf6ce0fb3003997a"],"modifiedAt":1757701473449,"zIndex":19,"figureId":null},{"id":"bacb67df1b37b6f15c426d449e91fd42","type":"rectangle","containerId":"7e83ad5eb0c5e2863a38ad36d104ed31","diagramId":"hm9oDFve7ngqKoMLiKf82","diagramEntityId":"Restart Tomcat Server","diagramRole":"node","strokeColor":"#242424","backgroundColor":"#c0f8d0","fillStyle":"solid","strokeWidth":0.75,"strokeStyle":"solid","strokeSharpness":[6,6,6,6],"roughness":0,"opacity":100,"elementStyle":1,"colorMode":0,"x":450,"y":502,"shapeVersion":"v2","compound":{"type":"parent","containerType":"flow-node","settings":{"shape":"rectangle","color":"green","colorMode":"pastel","styleMode":"shadow","typeface":"rough"},"children":{"label":"Restart Tomcat\nServer","icon":{"name":"refresh-cw"}}},"width":138,"height":72,"angle":0,"groupIds":[],"lockedGroupId":null,"seed":337895815,"version":24,"versionNonce":507749257,"isDeleted":false,"boundElementIds":["1624ae739f06a4cdaf6ce0fb3003997a","715885ceca7435b82e8657eac8979200"],"modifiedAt":1757701473449,"zIndex":21,"figureId":null},{"id":"b845e29c8239938cc79f88e9105e965d","strokeColor":"#c43dcf","backgroundColor":"rgba(252,247,253, 1)","fillStyle":"solid","strokeWidth":0.75,"strokeStyle":"solid","strokeSharpness":"round","roughness":0,"opacity":100,"elementStyle":1,"colorMode":0,"diagramId":"hm9oDFve7ngqKoMLiKf82","diagramEntityId":"Application Live","type":"rectangle","isContainer":true,"diagramRole":"group","sizingMode":"manual","compound":{"type":"parent","containerType":"group","settings":{"color":"purple","colorMode":"pastel","styleMode":"shadow","typeface":"rough"},"children":{"label":"APPLICATION LIVE","icon":{"name":"server"}}},"x":696,"y":427,"width":409,"height":189.33339436848962,"angle":0,"groupIds":[],"lockedGroupId":null,"seed":1487075591,"version":35,"versionNonce":420327879,"isDeleted":false,"boundElementIds":null,"modifiedAt":1757701507626,"zIndex":23,"figureId":null,"options":{"sizingMode":"manual"}},{"id":"ef26f07bc94beb9356777baf4ce28460","type":"oval","containerId":"b845e29c8239938cc79f88e9105e965d","diagramId":"hm9oDFve7ngqKoMLiKf82","diagramEntityId":"Application Running on Tomcat","diagramRole":"node","strokeColor":"#242424","backgroundColor":"#000000","fillStyle":"solid","strokeWidth":0.75,"strokeStyle":"solid","strokeSharpness":"round","roughness":0,"opacity":100,"elementStyle":1,"colorMode":0,"x":733,"y":476,"shapeVersion":"v2","compound":{"type":"parent","containerType":"flow-node","settings":{"shape":"oval","color":"lightpurple","colorMode":"pastel","styleMode":"shadow","typeface":"rough"},"children":{"label":"Application\nRunning on\nTomcat","icon":{"name":"server"}}},"width":138,"height":124.2,"angle":0,"groupIds":[],"lockedGroupId":null,"seed":1668111079,"version":25,"versionNonce":1935060135,"isDeleted":false,"boundElementIds":["32b6162ae282e40ad4936d3150e42d00","715885ceca7435b82e8657eac8979200"],"modifiedAt":1757701473449,"zIndex":24,"figureId":null},{"id":"0aa1840389b9aefd648b185485e0f9e1","type":"rectangle","containerId":"b845e29c8239938cc79f88e9105e965d","diagramId":"hm9oDFve7ngqKoMLiKf82","diagramEntityId":"Accessible via EC2 Public IP","diagramRole":"node","strokeColor":"#242424","backgroundColor":"#f4c0f8","fillStyle":"solid","strokeWidth":0.75,"strokeStyle":"solid","strokeSharpness":[6,6,6,6],"roughness":0,"opacity":100,"elementStyle":1,"colorMode":0,"x":930,"y":502,"shapeVersion":"v2","compound":{"type":"parent","containerType":"flow-node","settings":{"shape":"rectangle","color":"purple","colorMode":"pastel","styleMode":"shadow","typeface":"rough"},"children":{"label":"Accessible via\nEC2 Public IP","icon":{"name":"globe"}}},"width":138,"height":72,"angle":0,"groupIds":[],"lockedGroupId":null,"seed":1054134343,"version":24,"versionNonce":1162379207,"isDeleted":false,"boundElementIds":["32b6162ae282e40ad4936d3150e42d00"],"modifiedAt":1757701473449,"zIndex":26,"figureId":null},{"id":"3a0bee441c8a827836d1f044c65ed0ff","type":"arrow","diagramId":"hm9oDFve7ngqKoMLiKf82","diagramEntityId":"rel-Developer Pushes Code-GitHub Repository-forward","strokeColor":"#000000","backgroundColor":"transparent","fillStyle":"solid","strokeWidth":0.75,"strokeStyle":"solid","strokeSharpness":"elbow","roughness":0,"opacity":100,"arrowHeadSize":12,"shouldApplyRoughness":true,"startArrowhead":null,"endArrowhead":"arrow","cardinalElbowData":{"isEnabled":true},"points":[[0,0],[55,0]],"x":187,"y":105,"diagramCodeElement":{"from":"Developer Pushes Code","to":"GitHub Repository","relationshipType":"FORWARD"},"lastCommittedPoint":null,"startBinding":{"elementId":"a9b4d2470968af6c987c5d7dcce45ade","bindingType":"portOrCenter","portLocationOptions":{"portLocation":"fixed.CustomPort","relativeOffset":[1.0289855072463767,-0.009661835748792407],"direction":"right"}},"endBinding":{"elementId":"fbd877b2637f6acf216574d89daa1d8d","bindingType":"portOrCenter","portLocationOptions":{"portLocation":"fixed.CustomPort","relativeOffset":[-1.0289855072463767,0],"direction":"left"}},"width":55,"height":0,"angle":0,"groupIds":[],"lockedGroupId":null,"seed":1623966119,"version":4,"versionNonce":935334823,"isDeleted":false,"boundElementIds":null,"modifiedAt":1757701098453,"zIndex":4,"figureId":null},{"id":"85f565864fa77778c81a6c5de192e189","type":"arrow","diagramId":"hm9oDFve7ngqKoMLiKf82","diagramEntityId":"rel-Jenkins Job Triggered-Clone Code from GitHub-forward","strokeColor":"#000000","backgroundColor":"transparent","fillStyle":"solid","strokeWidth":0.75,"strokeStyle":"solid","strokeSharpness":"elbow","roughness":0,"opacity":100,"arrowHeadSize":12,"shouldApplyRoughness":true,"startArrowhead":null,"endArrowhead":"arrow","cardinalElbowData":{"isEnabled":true},"points":[[0,0],[55,0]],"x":143,"y":311,"diagramCodeElement":{"from":"Jenkins Job Triggered","to":"Clone Code from GitHub","relationshipType":"FORWARD"},"lastCommittedPoint":null,"startBinding":{"elementId":"29a4a89457cde6f9b8ae27b172493af0","bindingType":"portOrCenter","portLocationOptions":{"portLocation":"fixed.CustomPort","relativeOffset":[1.0289855072463767,-0.00966183574879172],"direction":"right"}},"endBinding":{"elementId":"d2d0dfc360ac336a065d5bb6850ceb38","bindingType":"portOrCenter","portLocationOptions":{"portLocation":"fixed.CustomPort","relativeOffset":[-1.0287786285239295,0],"direction":"left"}},"width":55,"height":0,"angle":0,"groupIds":[],"lockedGroupId":null,"seed":1297282247,"version":15,"versionNonce":1004674439,"isDeleted":false,"boundElementIds":null,"modifiedAt":1757701357132,"zIndex":9,"figureId":null},{"id":"980546449d74f196ffaa1e927bed22a1","type":"arrow","diagramId":"hm9oDFve7ngqKoMLiKf82","diagramEntityId":"rel-Clone Code from GitHub-Pipeline as Code-forward","strokeColor":"#000000","backgroundColor":"transparent","fillStyle":"solid","strokeWidth":0.75,"strokeStyle":"solid","strokeSharpness":"elbow","roughness":0,"opacity":100,"arrowHeadSize":12,"shouldApplyRoughness":true,"startArrowhead":null,"endArrowhead":"arrow","cardinalElbowData":{"isEnabled":true},"points":[[0,0],[59,0]],"x":339,"y":311,"diagramCodeElement":{"from":"Clone Code from GitHub","to":"Pipeline as Code","relationshipType":"FORWARD"},"lastCommittedPoint":null,"startBinding":{"elementId":"d2d0dfc360ac336a065d5bb6850ceb38","bindingType":"portOrCenter","portLocationOptions":{"portLocation":"fixed.CustomPort","relativeOffset":[1.000114682413106,0],"direction":"right"}},"endBinding":{"elementId":"d4f4541c982eb493bca916ede0f526ad","bindingType":"portOrCenter","portLocationOptions":{"portLocation":"fixed.CustomPort","relativeOffset":[-1,0],"direction":"left"}},"width":59,"height":0,"angle":0,"groupIds":[],"lockedGroupId":null,"seed":488169257,"version":16,"versionNonce":694482985,"isDeleted":false,"boundElementIds":null,"modifiedAt":1757701429386,"zIndex":12,"figureId":null},{"id":"b37b66548fba25e634b8db665e124c3a","type":"arrow","diagramId":"hm9oDFve7ngqKoMLiKf82","diagramEntityId":"rel-Pipeline as Code-Build with Maven-forward","strokeColor":"#000000","backgroundColor":"transparent","fillStyle":"solid","strokeWidth":0.75,"strokeStyle":"solid","strokeSharpness":"elbow","roughness":0,"opacity":100,"arrowHeadSize":12,"shouldApplyRoughness":true,"startArrowhead":null,"endArrowhead":"arrow","cardinalElbowData":{"isEnabled":true},"points":[[0,0],[59,0]],"x":537,"y":311,"diagramCodeElement":{"from":"Pipeline as Code","to":"Build with Maven","relationshipType":"FORWARD"},"lastCommittedPoint":null,"startBinding":{"elementId":"d4f4541c982eb493bca916ede0f526ad","bindingType":"portOrCenter","portLocationOptions":{"portLocation":"fixed.CustomPort","relativeOffset":[1.0050338422029008,0],"direction":"right"}},"endBinding":{"elementId":"ebc26dd97a60bb8a5a773eea8a561c08","bindingType":"portOrCenter","portLocationOptions":{"portLocation":"fixed.CustomPort","relativeOffset":[-1,0],"direction":"left"}},"width":59,"height":0,"angle":0,"groupIds":[],"lockedGroupId":null,"seed":80135143,"version":16,"versionNonce":1168423655,"isDeleted":false,"boundElementIds":null,"modifiedAt":1757701429386,"zIndex":13,"figureId":null},{"id":"21c42561ba1488104c56bbe8210f00e0","type":"arrow","diagramId":"hm9oDFve7ngqKoMLiKf82","diagramEntityId":"rel-Package Artifact-Trigger Ansible Playbook-forward","strokeColor":"#000000","backgroundColor":"transparent","fillStyle":"solid","strokeWidth":0.75,"strokeStyle":"solid","strokeSharpness":"elbow","roughness":0,"opacity":100,"arrowHeadSize":12,"shouldApplyRoughness":true,"startArrowhead":null,"endArrowhead":"arrow","cardinalElbowData":{"isEnabled":true,"preferredSegmentDirections":["right","down","left","down","right"],"segmentHandleManualPositions":{"1":[74.99981689453125,null],"2":[null,100],"3":[-952,null]}},"points":[[0,0],[74.99981689453125,0],[74.99981689453125,100],[-952,100],[-952,227],[-929,227]],"x":979,"y":311,"diagramCodeElement":{"from":"Package Artifact","to":"Trigger Ansible Playbook","relationshipType":"FORWARD"},"lastCommittedPoint":null,"startBinding":{"elementId":"2fc35d4f44b6df811231ac162514dc9a","bindingType":"portOrCenter","portLocationOptions":{"portLocation":"fixed.CardinalDirection","direction":"right"},"portOrientation":"inwardOrOutward"},"endBinding":{"elementId":"06c0bc662a7b253df3d556a1e21d2d1d","bindingType":"portOrCenter","portLocationOptions":{"portLocation":"fixed.CardinalDirection","direction":"left"},"portOrientation":"inwardOrOutward"},"width":1026.9998168945312,"height":227,"angle":0,"groupIds":[],"lockedGroupId":null,"seed":659522217,"version":331,"versionNonce":1047736073,"isDeleted":false,"boundElementIds":null,"modifiedAt":1757701519502,"zIndex":18,"figureId":null},{"id":"49db2f34b1fccf7b3c2cb2e5244cf13a","type":"arrow","diagramId":"hm9oDFve7ngqKoMLiKf82","diagramEntityId":"rel-Trigger Ansible Playbook-Ansible Copies Artifact to Tomcat-forward","strokeColor":"#000000","backgroundColor":"transparent","fillStyle":"solid","strokeWidth":0.75,"strokeStyle":"solid","strokeSharpness":"elbow","roughness":0,"opacity":100,"arrowHeadSize":12,"shouldApplyRoughness":true,"startArrowhead":null,"endArrowhead":"arrow","cardinalElbowData":{"isEnabled":true},"points":[[0,0],[59,0]],"x":190,"y":538,"diagramCodeElement":{"from":"Trigger Ansible Playbook","to":"Ansible Copies Artifact to Tomcat","relationshipType":"FORWARD"},"lastCommittedPoint":null,"startBinding":{"elementId":"06c0bc662a7b253df3d556a1e21d2d1d","bindingType":"portOrCenter","portLocationOptions":{"portLocation":"fixed.CustomPort","relativeOffset":[1,0],"direction":"right"}},"endBinding":{"elementId":"a25606c0c57377fc96f4f78a77f79866","bindingType":"portOrCenter","portLocationOptions":{"portLocation":"fixed.CustomPort","relativeOffset":[-0.9999999999999996,0],"direction":"left"}},"width":59,"height":0,"angle":0,"groupIds":[],"lockedGroupId":null,"seed":1248323817,"version":20,"versionNonce":1799019111,"isDeleted":false,"boundElementIds":null,"modifiedAt":1757701473449,"zIndex":20,"figureId":null},{"id":"1624ae739f06a4cdaf6ce0fb3003997a","type":"arrow","diagramId":"hm9oDFve7ngqKoMLiKf82","diagramEntityId":"rel-Ansible Copies Artifact to Tomcat-Restart Tomcat Server-forward","strokeColor":"#000000","backgroundColor":"transparent","fillStyle":"solid","strokeWidth":0.75,"strokeStyle":"solid","strokeSharpness":"elbow","roughness":0,"opacity":100,"arrowHeadSize":12,"shouldApplyRoughness":true,"startArrowhead":null,"endArrowhead":"arrow","cardinalElbowData":{"isEnabled":true},"points":[[0,0],[59,0]],"x":391,"y":538,"diagramCodeElement":{"from":"Ansible Copies Artifact to Tomcat","to":"Restart Tomcat Server","relationshipType":"FORWARD"},"lastCommittedPoint":null,"startBinding":{"elementId":"a25606c0c57377fc96f4f78a77f79866","bindingType":"portOrCenter","portLocationOptions":{"portLocation":"fixed.CustomPort","relativeOffset":[0.9926664931401796,0],"direction":"right"}},"endBinding":{"elementId":"bacb67df1b37b6f15c426d449e91fd42","bindingType":"portOrCenter","portLocationOptions":{"portLocation":"fixed.CustomPort","relativeOffset":[-1,0],"direction":"left"}},"width":59,"height":0,"angle":0,"groupIds":[],"lockedGroupId":null,"seed":1595291175,"version":19,"versionNonce":333510023,"isDeleted":false,"boundElementIds":null,"modifiedAt":1757701473449,"zIndex":22,"figureId":null},{"id":"715885ceca7435b82e8657eac8979200","type":"arrow","diagramId":"hm9oDFve7ngqKoMLiKf82","diagramEntityId":"rel-Restart Tomcat Server-Application Running on Tomcat-forward","strokeColor":"#000000","backgroundColor":"transparent","fillStyle":"solid","strokeWidth":0.75,"strokeStyle":"solid","strokeSharpness":"elbow","roughness":0,"opacity":100,"arrowHeadSize":12,"shouldApplyRoughness":true,"startArrowhead":null,"endArrowhead":"arrow","cardinalElbowData":{"isEnabled":true},"points":[[0,0],[143,0]],"x":588,"y":538,"diagramCodeElement":{"from":"Restart Tomcat Server","to":"Application Running on Tomcat","relationshipType":"FORWARD"},"lastCommittedPoint":null,"startBinding":{"elementId":"bacb67df1b37b6f15c426d449e91fd42","bindingType":"portOrCenter","portLocationOptions":{"portLocation":"fixed.CustomPort","relativeOffset":[1,0],"direction":"right"}},"endBinding":{"elementId":"ef26f07bc94beb9356777baf4ce28460","bindingType":"portOrCenter","portLocationOptions":{"portLocation":"fixed.CustomPort","relativeOffset":[-1.0289855072463767,-0.0016103059581324107],"direction":"left"}},"width":143,"height":0,"angle":0,"groupIds":[],"lockedGroupId":null,"seed":1499338855,"version":19,"versionNonce":339023177,"isDeleted":false,"boundElementIds":null,"modifiedAt":1757701473449,"zIndex":25,"figureId":null},{"id":"32b6162ae282e40ad4936d3150e42d00","type":"arrow","diagramId":"hm9oDFve7ngqKoMLiKf82","diagramEntityId":"rel-Application Running on Tomcat-Accessible via EC2 Public IP-forward","strokeColor":"#000000","backgroundColor":"transparent","fillStyle":"solid","strokeWidth":0.75,"strokeStyle":"solid","strokeSharpness":"elbow","roughness":0,"opacity":100,"arrowHeadSize":12,"shouldApplyRoughness":true,"startArrowhead":null,"endArrowhead":"arrow","cardinalElbowData":{"isEnabled":true},"points":[[0,0],[55,0]],"x":873,"y":538,"diagramCodeElement":{"from":"Application Running on Tomcat","to":"Accessible via EC2 Public IP","relationshipType":"FORWARD"},"lastCommittedPoint":null,"startBinding":{"elementId":"ef26f07bc94beb9356777baf4ce28460","bindingType":"portOrCenter","portLocationOptions":{"portLocation":"fixed.CustomPort","relativeOffset":[1.0289855072463767,-0.0016103059581324107],"direction":"right"}},"endBinding":{"elementId":"0aa1840389b9aefd648b185485e0f9e1","bindingType":"portOrCenter","portLocationOptions":{"portLocation":"fixed.CustomPort","relativeOffset":[-1.0289855072463767,0],"direction":"left"}},"width":55,"height":0,"angle":0,"groupIds":[],"lockedGroupId":null,"seed":1831658441,"version":19,"versionNonce":1901429801,"isDeleted":false,"boundElementIds":null,"modifiedAt":1757701473449,"zIndex":27,"figureId":null},{"id":"e16c2e50a829d367688841fa4ffcb2a6","type":"arrow","diagramId":"hm9oDFve7ngqKoMLiKf82","diagramEntityId":"rel-GitHub Repository-Jenkins Job Triggered-forward","strokeColor":"#000000","backgroundColor":"transparent","fillStyle":"solid","strokeWidth":0.75,"strokeStyle":"solid","strokeSharpness":"elbow","roughness":0,"opacity":100,"arrowHeadSize":12,"shouldApplyRoughness":true,"startArrowhead":null,"endArrowhead":"arrow","cardinalElbowData":{"isEnabled":true,"preferredSegmentDirections":["down","left","down","left"]},"points":[[0,0],[0,110],[-140,110],[-140,135],[-172,135]],"x":313,"y":141,"diagramCodeElement":{"from":"GitHub Repository","to":"Jenkins Job Triggered","relationshipType":"FORWARD"},"lastCommittedPoint":null,"startBinding":{"elementId":"fbd877b2637f6acf216574d89daa1d8d","bindingType":"portOrCenter","portLocationOptions":{"portLocation":"varying.CardinalDirection","preferredDirection":"down"}},"endBinding":{"elementId":"29a4a89457cde6f9b8ae27b172493af0","bindingType":"portOrCenter","portLocationOptions":{"portLocation":"varying.CardinalDirection","preferredDirection":"right"}},"width":172,"height":135,"angle":0,"groupIds":[],"lockedGroupId":null,"seed":564453097,"version":4,"versionNonce":1825768263,"isDeleted":false,"boundElementIds":null,"zIndex":7,"modifiedAt":1757701357132,"figureId":null},{"id":"066ae7b08320ff91f3c7ceca8b77dfa6","type":"arrow","diagramId":"hm9oDFve7ngqKoMLiKf82","diagramEntityId":"rel-Build with Maven-Package Artifact-forward","strokeColor":"#000000","backgroundColor":"transparent","fillStyle":"solid","strokeWidth":0.75,"strokeStyle":"solid","strokeSharpness":"elbow","roughness":0,"opacity":100,"arrowHeadSize":12,"shouldApplyRoughness":true,"startArrowhead":null,"endArrowhead":"arrow","cardinalElbowData":{"isEnabled":true,"preferredSegmentDirections":["right"],"segmentHandleManualPositions":{}},"points":[[0,0],[105,0]],"x":734,"y":311,"diagramCodeElement":{"from":"Build with Maven","to":"Package Artifact","relationshipType":"FORWARD"},"lastCommittedPoint":null,"startBinding":{"elementId":"ebc26dd97a60bb8a5a773eea8a561c08","bindingType":"portOrCenter","portLocationOptions":{"portLocation":"varying.CardinalDirection","preferredDirection":"right"},"portOrientation":"outward"},"endBinding":{"elementId":"2fc35d4f44b6df811231ac162514dc9a","bindingType":"portOrCenter","portLocationOptions":{"portLocation":"varying.CardinalDirection","preferredDirection":"left"},"portOrientation":"outward"},"width":105,"height":0,"angle":0,"groupIds":[],"lockedGroupId":null,"seed":875624135,"version":213,"versionNonce":638586599,"isDeleted":false,"boundElementIds":null,"zIndex":15,"modifiedAt":1757701482182,"figureId":null}],"diagramMetadata":{"settings":{"colorMode":"pastel","styleMode":"shadow","typeface":"rough","direction":"right"},"diagramType":"flowchart-diagram","diagramId":"hm9oDFve7ngqKoMLiKf82","connections":[{"from":"Developer Pushes Code","to":"GitHub Repository","connectionType":">"},{"from":"GitHub Repository","to":"Jenkins Job Triggered","connectionType":">"},{"from":"Jenkins Job Triggered","to":"Clone Code from GitHub","connectionType":">"},{"from":"Clone Code from GitHub","to":"Pipeline as Code","connectionType":">"},{"from":"Pipeline as Code","to":"Build with Maven","connectionType":">"},{"from":"Build with Maven","to":"Package Artifact","connectionType":">"},{"from":"Package Artifact","to":"Trigger Ansible Playbook","connectionType":">"},{"from":"Trigger Ansible Playbook","to":"Ansible Copies Artifact to Tomcat","connectionType":">"},{"from":"Ansible Copies Artifact to Tomcat","to":"Restart Tomcat Server","connectionType":">"},{"from":"Restart Tomcat Server","to":"Application Running on Tomcat","connectionType":">"},{"from":"Application Running on Tomcat","to":"Accessible via EC2 Public IP","connectionType":">"}],"entitySettings":{"Source Code Management":{"colorMode":"pastel","styleMode":"shadow","typeface":"rough","icon":"github","color":"blue"},"Developer Pushes Code":{"colorMode":"pastel","styleMode":"shadow","typeface":"rough","icon":"user","color":"lightblue","shape":"oval"},"GitHub Repository":{"colorMode":"pastel","styleMode":"shadow","typeface":"rough","color":"blue","icon":"github"},"Continuous Integration":{"colorMode":"pastel","styleMode":"shadow","typeface":"rough","icon":"jenkins","color":"orange"},"Jenkins Job Triggered":{"colorMode":"pastel","styleMode":"shadow","typeface":"rough","icon":"jenkins","color":"orange","shape":"oval"},"Clone Code from GitHub":{"colorMode":"pastel","styleMode":"shadow","typeface":"rough","color":"orange","icon":"github"},"Build with Maven":{"colorMode":"pastel","styleMode":"shadow","typeface":"rough","color":"orange","icon":"package"},"Pipeline as Code":{"colorMode":"pastel","styleMode":"shadow","typeface":"rough","color":"orange","icon":"file-text"},"Package Artifact":{"colorMode":"pastel","styleMode":"shadow","typeface":"rough","color":"orange","icon":"archive"},"Continuous Deployment":{"colorMode":"pastel","styleMode":"shadow","typeface":"rough","icon":"play-circle","color":"green"},"Trigger Ansible Playbook":{"colorMode":"pastel","styleMode":"shadow","typeface":"rough","color":"green","icon":"play"},"Ansible Copies Artifact to Tomcat":{"colorMode":"pastel","styleMode":"shadow","typeface":"rough","color":"green","icon":"upload"},"Restart Tomcat Server":{"colorMode":"pastel","styleMode":"shadow","typeface":"rough","color":"green","icon":"refresh-cw"},"Application Live":{"colorMode":"pastel","styleMode":"shadow","typeface":"rough","icon":"server","color":"purple"},"Application Running on Tomcat":{"colorMode":"pastel","styleMode":"shadow","typeface":"rough","icon":"server","color":"lightpurple","shape":"oval"},"Accessible via EC2 Public IP":{"colorMode":"pastel","styleMode":"shadow","typeface":"rough","color":"purple","icon":"globe"}}}}

# Small-Scale CI/CD Project on AWS

![CI/CD Pipeline Banner](https://via.placeholder.com/1200x300?text=CI/CD+Pipeline+on+AWS) <!-- Replace with actual banner image if available -->

## Table of Contents

- [Project Overview](#project-overview)
- [Infrastructure Setup](#infrastructure-setup)
- [Source Code Management](#source-code-management)
- [CI/CD Pipeline Configuration](#cicd-pipeline-configuration)
- [Deployment Workflow](#deployment-workflow)
- [Security and Networking](#security-and-networking)
- [Challenges and Resolutions](#challenges-and-resolutions)
- [Future Improvements](#future-improvements)

## Project Overview

This project demonstrates a simple end-to-end CI/CD pipeline for a Java-based web application deployed on AWS. The goal is to automate the build, test, and deployment process, showcasing DevOps practices in a small-scale environment. 

### Key Objectives:
- Automate code integration and deployment upon GitHub commits.
- Use open-source tools for building and deploying artifacts.
- Host everything on a single AWS EC2 instance for simplicity.

### Tech Stack:
- **AWS EC2**: For hosting the Jenkins server, Tomcat, and the application.
- **Maven**: Build tool for compiling and packaging the Java application.
- **Jenkins**: CI/CD server to orchestrate the pipeline.
- **Ansible**: Configuration management tool for deploying artifacts to Tomcat.
- **Tomcat**: Application server to host the deployed WAR file.
- **GitHub**: Source code repository with webhook integration.

The application is a basic Java web app (e.g., a simple servlet-based "Hello World" app).

## Infrastructure Setup

### EC2 Instance Creation
1. Log in to the AWS Management Console.
2. Navigate to EC2 Dashboard > Launch Instance.
3. Choose an Amazon Linux 2 AMI (free tier eligible).
4. Select t2.micro instance type.
5. Use default VPC and subnets (auto-assign public IP enabled).
6. Add storage: Default 8 GiB gp2 volume.
7. Add tags (e.g., Name: "CI-CD-Server").
8. Configure security group:
   - Allow SSH (port 22) from your IP.
   - Allow HTTP (port 80) from anywhere (0.0.0.0/0).
   - Allow Jenkins UI (port 8080) from your IP.
   - Allow Tomcat (port 8081) if customized, from anywhere.
9. Launch with a new or existing key pair for SSH access.

### Manual Installation via EC2 Terminal
Connect to the EC2 instance via SSH (e.g., `ssh -i key.pem ec2-user@public-ip`).

#### Install Java (required for Maven, Jenkins, Tomcat):
```bash
sudo yum update -y
sudo yum install java-1.8.0-openjdk -y
```

#### Install Maven:
```bash
sudo wget https://repos.fedorapeople.org/repos/dchen/apache-maven/epel-apache-maven.repo -O /etc/yum.repos.d/epel-apache-maven.repo
sudo sed -i s/\$releasever/6/g /etc/yum.repos.d/epel-apache-maven.repo
sudo yum install -y apache-maven
mvn -version  # Verify installation
```

#### Install Jenkins:
```bash
sudo wget -O /etc/yum.repos.d/jenkins.repo https://pkg.jenkins.io/redhat-stable/jenkins.repo
sudo rpm --import https://pkg.jenkins.io/redhat-stable/jenkins.io-2023.key
sudo yum upgrade -y
sudo yum install jenkins -y
sudo systemctl start jenkins
sudo systemctl enable jenkins
```

Access Jenkins UI at `http://<ec2-public-ip>:8080` and complete initial setup (unlock with admin password from `/var/lib/jenkins/secrets/initialAdminPassword`).

#### Install Ansible:
```bash
sudo amazon-linux-extras install ansible2 -y
ansible --version  # Verify
```

#### Install Tomcat:
```bash
sudo yum install tomcat -y
sudo systemctl start tomcat
sudo systemctl enable tomcat
```

### Security Group Configuration
- Inbound Rules:
  - SSH: TCP 22, My IP
  - HTTP: TCP 80, 0.0.0.0/0
  - Jenkins: TCP 8080, My IP
  - Tomcat: TCP 8080 (default Tomcat port; adjust if needed), 0.0.0.0/0
- Outbound: All traffic allowed.

## Source Code Management

### GitHub Repository Setup
1. Create a new repository on GitHub (e.g., `ci-cd-demo`).
2. Clone locally: `git clone https://github.com/<username>/ci-cd-demo.git`.
3. Add your Java app source code, including `pom.xml` for Maven.
4. Commit and push: `git add . && git commit -m "Initial commit" && git push origin main`.

### Webhook Configuration
1. In GitHub repo > Settings > Webhooks > Add webhook.
2. Payload URL: `http://<ec2-public-ip>:8080/github-webhook/`
3. Content type: application/json
4. Events: Just the push event.
5. Active: Checked.
6. Add webhook.

Ensure Jenkins has the GitHub plugin installed (via Manage Jenkins > Manage Plugins).

## CI/CD Pipeline Configuration

### Jenkins Setup and Job Creation
1. Install necessary plugins: GitHub Integration, Maven Integration, Ansible.
2. Create a new Pipeline job: New Item > Pipeline > OK.
3. In Pipeline definition, select "Pipeline script from SCM".
4. SCM: Git, Repository URL: `https://github.com/<username>/ci-cd-demo.git`.
5. Script Path: `Jenkinsfile`.
6. Build Triggers: GitHub hook trigger for GITScm polling.

### Maven Integration
Maven is used to build the app. Ensure `pom.xml` is in the repo root.

Example `pom.xml` snippet:
```xml
<project>
    <groupId>com.example</groupId>
    <artifactId>demo-app</artifactId>
    <version>1.0-SNAPSHOT</version>
    <packaging>war</packaging>
    <!-- Dependencies and plugins here -->
</project>
```

In Jenkinsfile, add a stage for Maven build.

### Ansible Playbook for Deployment
Create an Ansible playbook in the repo (e.g., `deploy.yml`).

Example `deploy.yml`:
```yaml
---
- name: Deploy to Tomcat
  hosts: localhost
  tasks:
    - name: Copy WAR to Tomcat
      copy:
        src: target/demo-app.war
        dest: /var/lib/tomcat/webapps/
        remote_src: yes
    - name: Restart Tomcat
      service:
        name: tomcat
        state: restarted
```

In Jenkinsfile, invoke Ansible after build.

## Deployment Workflow

### Step-by-Step Flow
1. **GitHub Commit**: Developer pushes code to the main branch.
2. **Jenkins Trigger**: Webhook notifies Jenkins, triggering the pipeline.
3. **Maven Build**: Jenkins checks out code, runs `mvn clean package` to build WAR.
4. **Ansible Deploy**: Ansible copies the WAR to Tomcat's webapps directory and restarts Tomcat.
5. **Tomcat Serve**: Application is live at `http://<ec2-public-ip>:8080/demo-app`.

### Code Snippets

#### Jenkinsfile
```groovy
pipeline {
    agent any
    stages {
        stage('Build') {
            steps {
                sh 'mvn clean package'
            }
        }
        stage('Deploy') {
            steps {
                ansiblePlaybook(
                    playbook: 'deploy.yml',
                    inventory: 'localhost,',
                    become: true
                )
            }
        }
    }
}
```

#### Ansible Playbook (deploy.yml)
See above example.

#### Maven Configuration (pom.xml)
See above snippet.

<!-- Add screenshots here if uploading images to repo, e.g., ![Jenkins Pipeline](images/jenkins-pipeline.png) -->

## Security and Networking

### IAM Roles and Key Pairs
- No custom IAM roles used; default EC2 instance profile.
- Key pair for SSH access: Generated during launch, stored securely.
- Network Access: Security groups restrict inbound traffic. VPC defaults used—no custom subnets or NACLs.

### Best Practices
- EC2: Use key-based SSH, disable password auth in `/etc/ssh/sshd_config`.
- Jenkins: Secure with user authentication (enable Security in Global Security). Use HTTPS if production-ready.
- General: Regularly update packages (`yum update`). Monitor logs with CloudWatch. Avoid running services as root.

## Challenges and Resolutions

- **EC2 Connectivity Issues**: SSH connection refused—Resolution: Verify security group allows port 22 from your IP; check instance public IP.
- **Jenkins Build Errors**: Maven not found—Resolution: Ensure Maven is in PATH; add `export PATH=$PATH:/opt/maven/bin` in Jenkins config or use Maven tool in Jenkins.
- **Ansible Deployment Issues**: Permission denied on Tomcat dir—Resolution: Run Ansible with `become: true` for sudo privileges; ensure ec2-user in tomcat group (`sudo usermod -aG tomcat ec2-user`).
- **Webhook Failures**: 404 on webhook—Resolution: Install GitHub plugin in Jenkins and ensure port 8080 is open.

## Future Improvements

- **Infrastructure as Code**: Use Terraform to automate EC2 creation and configuration for reproducibility.
- **Code Quality**: Integrate SonarQube in the Jenkins pipeline for static code analysis.
- **Containerization**: Dockerize the app and use ECS or EKS for deployment instead of direct Tomcat.
- **Scaling**: Separate Jenkins and Tomcat to different instances; add auto-scaling groups.
- **Monitoring**: Integrate Prometheus/Grafana for metrics and alerts.
- **Secrets Management**: Use AWS Secrets Manager for credentials instead of hardcoding.

---

This README is designed to be editable and self-contained. Feel free to fork the repo, add your screenshots, and customize! If you have questions, open an issue.

*Built with ❤️ by [Your Name] | LinkedIn: [Your LinkedIn] | Date: September 12, 2025*
