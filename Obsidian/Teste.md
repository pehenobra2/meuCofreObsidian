11:12:58,221 ERROR [stderr] (default task-88) java.net.UnknownHostException: analytics-psim-prod.bbts.com.br

  

11:12:58,222 ERROR [stderr] (default task-88) at java.net.Inet4AddressImpl.lookupAllHostAddr(Native Method)

  

11:12:58,222 ERROR [stderr] (default task-88) at java.net.InetAddress$2.lookupAllHostAddr(InetAddress.java:928)

  

11:12:58,222 ERROR [stderr] (default task-88) at java.net.InetAddress.getAddressesFromNameService(InetAddress.java:1323)

  

11:12:58,222 ERROR [stderr] (default task-88) at java.net.InetAddress.getAllByName0(InetAddress.java:1276)

  

11:12:58,223 ERROR [stderr] (default task-88) at java.net.InetAddress.getAllByName(InetAddress.java:1192)

  

11:12:58,223 ERROR [stderr] (default task-88) at java.net.InetAddress.getAllByName(InetAddress.java:1126)

  

11:12:58,223 ERROR [stderr] (default task-88) at org.apache.http.impl.conn.SystemDefaultDnsResolver.resolve(SystemDefaultDnsResolver.java:45)

  

11:12:58,223 ERROR [stderr] (default task-88) at org.apache.http.impl.conn.DefaultHttpClientConnectionOperator.connect(DefaultHttpClientConnectionOperator.java:112)

  

11:12:58,223 ERROR [stderr] (default task-88) at org.apache.http.impl.conn.PoolingHttpClientConnectionManager.connect(PoolingHttpClientConnectionManager.java:353)

  

11:12:58,223 ERROR [stderr] (default task-88) at org.apache.http.impl.execchain.MainClientExec.establishRoute(MainClientExec.java:380)

  

11:12:58,223 ERROR [stderr] (default task-88) at org.apache.http.impl.execchain.MainClientExec.execute(MainClientExec.java:236)

  

11:12:58,223 ERROR [stderr] (default task-88) at org.apache.http.impl.execchain.ProtocolExec.execute(ProtocolExec.java:184)

  

11:12:58,223 ERROR [stderr] (default task-88) at org.apache.http.impl.execchain.RetryExec.execute(RetryExec.java:88)

  

11:12:58,223 ERROR [stderr] (default task-88) at org.apache.http.impl.execchain.RedirectExec.execute(RedirectExec.java:110)

  

11:12:58,223 ERROR [stderr] (default task-88) at org.apache.http.impl.client.InternalHttpClient.doExecute(InternalHttpClient.java:184)

  

11:12:58,223 ERROR [stderr] (default task-88) at org.apache.http.impl.client.CloseableHttpClient.execute(CloseableHttpClient.java:82)

  

11:12:58,223 ERROR [stderr] (default task-88) at org.apache.http.impl.client.CloseableHttpClient.execute(CloseableHttpClient.java:107)

  

11:12:58,223 ERROR [stderr] (default task-88) at br.bbts.psim.integracao.mad.api.ApiMAD.getResponse(ApiMAD.java:167)

  

11:12:58,223 ERROR [stderr] (default task-88) at br.bbts.psim.integracao.mad.api.ApiMAD.executarPost(ApiMAD.java:77)

  

11:12:58,223 ERROR [stderr] (default task-88) at br.bbts.psim.integracao.mad.api.ApiMAD.executar(ApiMAD.java:58)

  

11:12:58,223 ERROR [stderr] (default task-88) at br.bbts.psim.controlador.relatorio.ControladorModuloInteligenteMAD.solicitarTokenEGuardar(ControladorModuloInteligenteMAD.java:163)

  

11:12:58,223 ERROR [stderr] (default task-88) at br.bbts.psim.controlador.relatorio.ControladorModuloInteligenteMAD.prepararListagem(ControladorModuloInteligenteMAD.java:150)

  

11:12:58,223 ERROR [stderr] (default task-88) at br.bbts.psim.controlador.relatorio.ControladorModuloInteligenteMAD.acaoIniciar(ControladorModuloInteligenteMAD.java:106)

  

11:12:58,223 ERROR [stderr] (default task-88) at sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method)

  

11:12:58,223 ERROR [stderr] (default task-88) at sun.reflect.NativeMethodAccessorImpl.invoke(NativeMethodAccessorImpl.java:62)

  

11:12:58,223 ERROR [stderr] (default task-88) at sun.reflect.DelegatingMethodAccessorImpl.invoke(DelegatingMethodAccessorImpl.java:43)

  

11:12:58,223 ERROR [stderr] (default task-88) at java.lang.reflect.Method.invoke(Method.java:498)

  

11:12:58,223 ERROR [stderr] (default task-88) at javax.el.ELUtil.invokeMethod(ELUtil.java:300)

  

11:12:58,223 ERROR [stderr] (default task-88) at sun.reflect.GeneratedMethodAccessor126.invoke(Unknown Source)

  

11:12:58,223 ERROR [stderr] (default task-88) at sun.reflect.DelegatingMethodAccessorImpl.invoke(DelegatingMethodAccessorImpl.java:43)

  

11:12:58,223 ERROR [stderr] (default task-88) at java.lang.reflect.Method.invoke(Method.java:498)

  

11:12:58,223 ERROR [stderr] (default task-88) at br.bbts.psim.util.CachedMethodsELResolver.chamarMetodo(CachedMethodsELResolver.java:112)

  

11:12:58,223 ERROR [stderr] (default task-88) at br.bbts.psim.util.CachedMethodsELResolver.invoke(CachedMethodsELResolver.java:84)

  

11:12:58,223 ERROR [stderr] (default task-88) at javax.el.CompositeELResolver.invoke(CompositeELResolver.java:256)

  

11:12:58,223 ERROR [stderr] (default task-88) at com.sun.el.parser.AstValue.invoke(AstValue.java:285)

  

11:12:58,223 ERROR [stderr] (default task-88) at com.sun.el.MethodExpressionImpl.invoke(MethodExpressionImpl.java:304)

  

11:12:58,223 ERROR [stderr] (default task-88) at org.jboss.weld.util.el.ForwardingMethodExpression.invoke(ForwardingMethodExpression.java:40)

  

11:12:58,223 ERROR [stderr] (default task-88) at org.jboss.weld.el.WeldMethodExpression.invoke(WeldMethodExpression.java:50)

  

11:12:58,225 ERROR [stderr] (default task-88) at org.jboss.weld.util.el.ForwardingMethodExpression.invoke(ForwardingMethodExpression.java:40)

  

11:12:58,225 ERROR [stderr] (default task-88) at org.jboss.weld.el.WeldMethodExpression.invoke(WeldMethodExpression.java:50)

  

11:12:58,225 ERROR [stderr] (default task-88) at org.primefaces.component.menu.AbstractMenu.broadcast(AbstractMenu.java:107)

  

11:12:58,225 ERROR [stderr] (default task-88) at javax.faces.component.UIViewRoot.broadcastEvents(UIViewRoot.java:790)

  

11:12:58,225 ERROR [stderr] (default task-88) at javax.faces.component.UIViewRoot.processDecodes(UIViewRoot.java:931)

  

11:12:58,225 ERROR [stderr] (default task-88) at com.sun.faces.lifecycle.ApplyRequestValuesPhase.execute(ApplyRequestValuesPhase.java:78)

  

11:12:58,225 ERROR [stderr] (default task-88) at com.sun.faces.lifecycle.Phase.doPhase(Phase.java:101)

  

11:12:58,225 ERROR [stderr] (default task-88) at com.sun.faces.lifecycle.LifecycleImpl.execute(LifecycleImpl.java:198)

  

11:12:58,225 ERROR [stderr] (default task-88) at javax.faces.webapp.FacesServlet.service(FacesServlet.java:658)

  

11:12:58,225 ERROR [stderr] (default task-88) at io.undertow.servlet.handlers.ServletHandler.handleRequest(ServletHandler.java:85)

  

11:12:58,225 ERROR [stderr] (default task-88) at io.undertow.servlet.handlers.FilterHandler$FilterChainImpl.doFilter(FilterHandler.java:129)

  

11:12:58,225 ERROR [stderr] (default task-88) at io.undertow.websockets.jsr.JsrWebSocketFilter.doFilter(JsrWebSocketFilter.java:130)

  

11:12:58,225 ERROR [stderr] (default task-88) at io.undertow.servlet.core.ManagedFilter.doFilter(ManagedFilter.java:61)

  

11:12:58,225 ERROR [stderr] (default task-88) at io.undertow.servlet.handlers.FilterHandler$FilterChainImpl.doFilter(FilterHandler.java:131)

  

11:12:58,225 ERROR [stderr] (default task-88) at com.codahale.metrics.servlet.AbstractInstrumentedFilter.doFilter(AbstractInstrumentedFilter.java:112)

  

11:12:58,225 ERROR [stderr] (default task-88) at io.undertow.servlet.core.ManagedFilter.doFilter(ManagedFilter.java:61)

  

11:12:58,225 ERROR [stderr] (default task-88) at io.undertow.servlet.handlers.FilterHandler$FilterChainImpl.doFilter(FilterHandler.java:131)

  

11:12:58,225 ERROR [stderr] (default task-88) at br.bbts.psim.filter.PSIMRedirectToHttpsFilter.doFilter(PSIMRedirectToHttpsFilter.java:30)

  

11:12:58,225 ERROR [stderr] (default task-88) at io.undertow.servlet.core.ManagedFilter.doFilter(ManagedFilter.java:61)

  

11:12:58,225 ERROR [stderr] (default task-88) at io.undertow.servlet.handlers.FilterHandler$FilterChainImpl.doFilter(FilterHandler.java:131)

  

11:12:58,225 ERROR [stderr] (default task-88) at br.bbts.psim.filter.PSIMAutenticadorFilter.continuarCadeiaDeFiltro(PSIMAutenticadorFilter.java:329)

  

11:12:58,225 ERROR [stderr] (default task-88) at br.bbts.psim.filter.PSIMAutenticadorFilter.doFilter(PSIMAutenticadorFilter.java:101)

  

11:12:58,225 ERROR [stderr] (default task-88) at io.undertow.servlet.core.ManagedFilter.doFilter(ManagedFilter.java:61)

  

11:12:58,225 ERROR [stderr] (default task-88) at io.undertow.servlet.handlers.FilterHandler$FilterChainImpl.doFilter(FilterHandler.java:131)

  

11:12:58,225 ERROR [stderr] (default task-88) at org.jboss.weld.servlet.ConversationFilter.doFilter(ConversationFilter.java:70)

  

11:12:58,225 ERROR [stderr] (default task-88) at io.undertow.servlet.core.ManagedFilter.doFilter(ManagedFilter.java:61)

  

11:12:58,226 ERROR [stderr] (default task-88) at io.undertow.servlet.handlers.FilterHandler$FilterChainImpl.doFilter(FilterHandler.java:131)

  

11:12:58,226 ERROR [stderr] (default task-88) at br.bbts.psim.filter.PSIMCDIConversationFilter.doFilter(PSIMCDIConversationFilter.java:46)

  

11:12:58,226 ERROR [stderr] (default task-88) at io.undertow.servlet.core.ManagedFilter.doFilter(ManagedFilter.java:61)

  

11:12:58,226 ERROR [stderr] (default task-88) at io.undertow.servlet.handlers.FilterHandler$FilterChainImpl.doFilter(FilterHandler.java:131)

  

11:12:58,226 ERROR [stderr] (default task-88) at org.primefaces.webapp.filter.FileUploadFilter.doFilter(FileUploadFilter.java:111)

  

11:12:58,226 ERROR [stderr] (default task-88) at io.undertow.servlet.core.ManagedFilter.doFilter(ManagedFilter.java:61)

  

11:12:58,226 ERROR [stderr] (default task-88) at io.undertow.servlet.handlers.FilterHandler$FilterChainImpl.doFilter(FilterHandler.java:131)

  

11:12:58,226 ERROR [stderr] (default task-88) at io.undertow.servlet.handlers.FilterHandler.handleRequest(FilterHandler.java:84)

  

11:12:58,226 ERROR [stderr] (default task-88) at io.undertow.servlet.handlers.security.ServletSecurityRoleHandler.handleRequest(ServletSecurityRoleHandler.java:62)

  

11:12:58,226 ERROR [stderr] (default task-88) at io.undertow.servlet.handlers.ServletDispatchingHandler.handleRequest(ServletDispatchingHandler.java:36)

  

11:12:58,226 ERROR [stderr] (default task-88) at org.wildfly.extension.undertow.security.SecurityContextAssociationHandler.handleRequest(SecurityContextAssociationHandler.java:78)

  

11:12:58,226 ERROR [stderr] (default task-88) at io.undertow.server.handlers.PredicateHandler.handleRequest(PredicateHandler.java:43)

  

11:12:58,226 ERROR [stderr] (default task-88) at io.undertow.servlet.handlers.security.SSLInformationAssociationHandler.handleRequest(SSLInformationAssociationHandler.java:131)

  

11:12:58,226 ERROR [stderr] (default task-88) at io.undertow.servlet.handlers.security.ServletAuthenticationCallHandler.handleRequest(ServletAuthenticationCallHandler.java:57)

  

11:12:58,226 ERROR [stderr] (default task-88) at io.undertow.server.handlers.PredicateHandler.handleRequest(PredicateHandler.java:43)

  

11:12:58,226 ERROR [stderr] (default task-88) at io.undertow.security.handlers.AbstractConfidentialityHandler.handleRequest(AbstractConfidentialityHandler.java:46)

  

11:12:58,226 ERROR [stderr] (default task-88) at io.undertow.servlet.handlers.security.ServletConfidentialityConstraintHandler.handleRequest(ServletConfidentialityConstraintHandler.java:64)

  

11:12:58,226 ERROR [stderr] (default task-88) at io.undertow.security.handlers.AuthenticationMechanismsHandler.handleRequest(AuthenticationMechanismsHandler.java:60)

  

11:12:58,226 ERROR [stderr] (default task-88) at io.undertow.servlet.handlers.security.CachedAuthenticatedSessionHandler.handleRequest(CachedAuthenticatedSessionHandler.java:77)

  

11:12:58,226 ERROR [stderr] (default task-88) at io.undertow.security.handlers.NotificationReceiverHandler.handleRequest(NotificationReceiverHandler.java:50)

  

11:12:58,226 ERROR [stderr] (default task-88) at io.undertow.security.handlers.AbstractSecurityContextAssociationHandler.handleRequest(AbstractSecurityContextAssociationHandler.java:43)

  

11:12:58,226 ERROR [stderr] (default task-88) at io.undertow.server.handlers.PredicateHandler.handleRequest(PredicateHandler.java:43)

  

11:12:58,226 ERROR [stderr] (default task-88) at org.wildfly.extension.undertow.security.jacc.JACCContextIdHandler.handleRequest(JACCContextIdHandler.java:61)

  

11:12:58,226 ERROR [stderr] (default task-88) at io.undertow.server.handlers.PredicateHandler.handleRequest(PredicateHandler.java:43)

  

11:12:58,226 ERROR [stderr] (default task-88) at io.undertow.server.handlers.PredicateHandler.handleRequest(PredicateHandler.java:43)

  

11:12:58,226 ERROR [stderr] (default task-88) at io.undertow.servlet.handlers.ServletInitialHandler.handleFirstRequest(ServletInitialHandler.java:285)

  

11:12:58,226 ERROR [stderr] (default task-88) at io.undertow.servlet.handlers.ServletInitialHandler.dispatchRequest(ServletInitialHandler.java:264)

  

11:12:58,226 ERROR [stderr] (default task-88) at io.undertow.servlet.handlers.ServletInitialHandler.access$000(ServletInitialHandler.java:81)

  

11:12:58,226 ERROR [stderr] (default task-88) at io.undertow.servlet.handlers.ServletInitialHandler$1.handleRequest(ServletInitialHandler.java:175)

  

11:12:58,226 ERROR [stderr] (default task-88) at io.undertow.server.Connectors.executeRootHandler(Connectors.java:202)

  

11:12:58,226 ERROR [stderr] (default task-88) at io.undertow.server.HttpServerExchange$1.run(HttpServerExchange.java:792)

  

11:12:58,227 ERROR [stderr] (default task-88) at java.util.concurrent.ThreadPoolExecutor.runWorker(ThreadPoolExecutor.java:1149)

  

11:12:58,227 ERROR [stderr] (default task-88) at java.util.concurrent.ThreadPoolExecutor$Worker.run(ThreadPoolExecutor.java:624)

  

11:12:58,227 ERROR [stderr] (default task-88) at java.lang.Thread.run(Thread.java:748)

  

11:12:58,227 WARNING [ControladorModuloInteligenteMAD] (default task-88) Falha na autenticação do serviço de integração MAD. Erro na conexão. java.net.UnknownHostException: analytics-psim-prod.bbts.com.br

11:12:58,319 ERROR [stderr] (default task-88) java.net.UnknownHostException: analytics-psim-prod.bbts.com.br

  

11:12:58,320 ERROR [stderr] (default task-88) at java.net.InetAddress.getAllByName0(InetAddress.java:1280)

  

11:12:58,320 ERROR [stderr] (default task-88) at java.net.InetAddress.getAllByName(InetAddress.java:1192)

  

11:12:58,321 ERROR [stderr] (default task-88) at java.net.InetAddress.getAllByName(InetAddress.java:1126)

  

11:12:58,321 ERROR [stderr] (default task-88) at org.apache.http.impl.conn.SystemDefaultDnsResolver.resolve(SystemDefaultDnsResolver.java:45)

  

11:12:58,321 ERROR [stderr] (default task-88) at org.apache.http.impl.conn.DefaultHttpClientConnectionOperator.connect(DefaultHttpClientConnectionOperator.java:112)

  

11:12:58,321 ERROR [stderr] (default task-88) at org.apache.http.impl.conn.PoolingHttpClientConnectionManager.connect(PoolingHttpClientConnectionManager.java:353)

  

11:12:58,321 ERROR [stderr] (default task-88) at org.apache.http.impl.execchain.MainClientExec.establishRoute(MainClientExec.java:380)

  

11:12:58,321 ERROR [stderr] (default task-88) at org.apache.http.impl.execchain.MainClientExec.execute(MainClientExec.java:236)

  

11:12:58,321 ERROR [stderr] (default task-88) at org.apache.http.impl.execchain.ProtocolExec.execute(ProtocolExec.java:184)

  

11:12:58,322 ERROR [stderr] (default task-88) at org.apache.http.impl.execchain.RetryExec.execute(RetryExec.java:88)

  

11:12:58,322 ERROR [stderr] (default task-88) at org.apache.http.impl.execchain.RedirectExec.execute(RedirectExec.java:110)

  

11:12:58,323 ERROR [stderr] (default task-88) at org.apache.http.impl.client.InternalHttpClient.doExecute(InternalHttpClient.java:184)

  

11:12:58,323 ERROR [stderr] (default task-88) at org.apache.http.impl.client.CloseableHttpClient.execute(CloseableHttpClient.java:82)

  

11:12:58,323 ERROR [stderr] (default task-88) at org.apache.http.impl.client.CloseableHttpClient.execute(CloseableHttpClient.java:107)

  

11:12:58,324 ERROR [stderr] (default task-88) at br.bbts.psim.integracao.mad.api.ApiMAD.getResponse(ApiMAD.java:167)

  

11:12:58,324 ERROR [stderr] (default task-88) at br.bbts.psim.integracao.mad.api.ApiMAD.executarGet(ApiMAD.java:108)

  

11:12:58,324 ERROR [stderr] (default task-88) at br.bbts.psim.integracao.mad.api.ApiMAD.executar(ApiMAD.java:61)

  

11:12:58,324 ERROR [stderr] (default task-88) at br.bbts.psim.controlador.relatorio.ControladorModuloInteligenteMAD.consultarColecao(ControladorModuloInteligenteMAD.java:184)

  

11:12:58,324 ERROR [stderr] (default task-88) at br.bbts.psim.controlador.relatorio.ControladorModuloInteligenteMAD.prepararListagem(ControladorModuloInteligenteMAD.java:152)

  

11:12:58,325 ERROR [stderr] (default task-88) at br.bbts.psim.controlador.relatorio.ControladorModuloInteligenteMAD.acaoIniciar(ControladorModuloInteligenteMAD.java:106)

  

11:12:58,325 ERROR [stderr] (default task-88) at sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method)

  

11:12:58,325 ERROR [stderr] (default task-88) at sun.reflect.NativeMethodAccessorImpl.invoke(NativeMethodAccessorImpl.java:62)

  

11:12:58,325 ERROR [stderr] (default task-88) at sun.reflect.DelegatingMethodAccessorImpl.invoke(DelegatingMethodAccessorImpl.java:43)

  

11:12:58,325 ERROR [stderr] (default task-88) at java.lang.reflect.Method.invoke(Method.java:498)

  

11:12:58,325 ERROR [stderr] (default task-88) at javax.el.ELUtil.invokeMethod(ELUtil.java:300)

  

11:12:58,325 ERROR [stderr] (default task-88) at sun.reflect.GeneratedMethodAccessor126.invoke(Unknown Source)

  

11:12:58,326 ERROR [stderr] (default task-88) at sun.reflect.DelegatingMethodAccessorImpl.invoke(DelegatingMethodAccessorImpl.java:43)

  

11:12:58,326 ERROR [stderr] (default task-88) at java.lang.reflect.Method.invoke(Method.java:498)

  

11:12:58,327 ERROR [stderr] (default task-88) at br.bbts.psim.util.CachedMethodsELResolver.chamarMetodo(CachedMethodsELResolver.java:112)

  

11:12:58,327 ERROR [stderr] (default task-88) at br.bbts.psim.util.CachedMethodsELResolver.invoke(CachedMethodsELResolver.java:84)

  

11:12:58,327 ERROR [stderr] (default task-88) at javax.el.CompositeELResolver.invoke(CompositeELResolver.java:256)

  

11:12:58,327 ERROR [stderr] (default task-88) at com.sun.el.parser.AstValue.invoke(AstValue.java:285)

  

11:12:58,327 ERROR [stderr] (default task-88) at com.sun.el.MethodExpressionImpl.invoke(MethodExpressionImpl.java:304)

  

11:12:58,327 ERROR [stderr] (default task-88) at org.jboss.weld.util.el.ForwardingMethodExpression.invoke(ForwardingMethodExpression.java:40)

  

11:12:58,327 ERROR [stderr] (default task-88) at org.jboss.weld.el.WeldMethodExpression.invoke(WeldMethodExpression.java:50)

  

11:12:58,327 ERROR [stderr] (default task-88) at org.jboss.weld.util.el.ForwardingMethodExpression.invoke(ForwardingMethodExpression.java:40)

  

11:12:58,327 ERROR [stderr] (default task-88) at org.jboss.weld.el.WeldMethodExpression.invoke(WeldMethodExpression.java:50)

  

11:12:58,327 ERROR [stderr] (default task-88) at org.primefaces.component.menu.AbstractMenu.broadcast(AbstractMenu.java:107)

  

11:12:58,327 ERROR [stderr] (default task-88) at javax.faces.component.UIViewRoot.broadcastEvents(UIViewRoot.java:790)

  

11:12:58,327 ERROR [stderr] (default task-88) at javax.faces.component.UIViewRoot.processDecodes(UIViewRoot.java:931)

  

11:12:58,327 ERROR [stderr] (default task-88) at com.sun.faces.lifecycle.ApplyRequestValuesPhase.execute(ApplyRequestValuesPhase.java:78)

  

11:12:58,327 ERROR [stderr] (default task-88) at com.sun.faces.lifecycle.Phase.doPhase(Phase.java:101)

  

11:12:58,327 ERROR [stderr] (default task-88) at com.sun.faces.lifecycle.LifecycleImpl.execute(LifecycleImpl.java:198)

  

11:12:58,328 ERROR [stderr] (default task-88) at javax.faces.webapp.FacesServlet.service(FacesServlet.java:658)

  

11:12:58,328 ERROR [stderr] (default task-88) at io.undertow.servlet.handlers.ServletHandler.handleRequest(ServletHandler.java:85)

  

11:12:58,328 ERROR [stderr] (default task-88) at io.undertow.servlet.handlers.FilterHandler$FilterChainImpl.doFilter(FilterHandler.java:129)

  

11:12:58,328 ERROR [stderr] (default task-88) at io.undertow.websockets.jsr.JsrWebSocketFilter.doFilter(JsrWebSocketFilter.java:130)

  

11:12:58,328 ERROR [stderr] (default task-88) at io.undertow.servlet.core.ManagedFilter.doFilter(ManagedFilter.java:61)

  

11:12:58,328 ERROR [stderr] (default task-88) at io.undertow.servlet.handlers.FilterHandler$FilterChainImpl.doFilter(FilterHandler.java:131)

  

11:12:58,328 ERROR [stderr] (default task-88) at com.codahale.metrics.servlet.AbstractInstrumentedFilter.doFilter(AbstractInstrumentedFilter.java:112)

  

11:12:58,328 ERROR [stderr] (default task-88) at io.undertow.servlet.core.ManagedFilter.doFilter(ManagedFilter.java:61)

  

11:12:58,328 ERROR [stderr] (default task-88) at io.undertow.servlet.handlers.FilterHandler$FilterChainImpl.doFilter(FilterHandler.java:131)

  

11:12:58,328 ERROR [stderr] (default task-88) at br.bbts.psim.filter.PSIMRedirectToHttpsFilter.doFilter(PSIMRedirectToHttpsFilter.java:30)

  

11:12:58,328 ERROR [stderr] (default task-88) at io.undertow.servlet.core.ManagedFilter.doFilter(ManagedFilter.java:61)

  

11:12:58,328 ERROR [stderr] (default task-88) at io.undertow.servlet.handlers.FilterHandler$FilterChainImpl.doFilter(FilterHandler.java:131)

  

11:12:58,328 ERROR [stderr] (default task-88) at br.bbts.psim.filter.PSIMAutenticadorFilter.continuarCadeiaDeFiltro(PSIMAutenticadorFilter.java:329)

  

11:12:58,328 ERROR [stderr] (default task-88) at br.bbts.psim.filter.PSIMAutenticadorFilter.doFilter(PSIMAutenticadorFilter.java:101)

  

11:12:58,328 ERROR [stderr] (default task-88) at io.undertow.servlet.core.ManagedFilter.doFilter(ManagedFilter.java:61)

  

11:12:58,328 ERROR [stderr] (default task-88) at io.undertow.servlet.handlers.FilterHandler$FilterChainImpl.doFilter(FilterHandler.java:131)

  

11:12:58,328 ERROR [stderr] (default task-88) at org.jboss.weld.servlet.ConversationFilter.doFilter(ConversationFilter.java:70)

  

11:12:58,328 ERROR [stderr] (default task-88) at io.undertow.servlet.core.ManagedFilter.doFilter(ManagedFilter.java:61)

  

11:12:58,328 ERROR [stderr] (default task-88) at io.undertow.servlet.handlers.FilterHandler$FilterChainImpl.doFilter(FilterHandler.java:131)

  

11:12:58,328 ERROR [stderr] (default task-88) at br.bbts.psim.filter.PSIMCDIConversationFilter.doFilter(PSIMCDIConversationFilter.java:46)

  

11:12:58,328 ERROR [stderr] (default task-88) at io.undertow.servlet.core.ManagedFilter.doFilter(ManagedFilter.java:61)

  

11:12:58,328 ERROR [stderr] (default task-88) at io.undertow.servlet.handlers.FilterHandler$FilterChainImpl.doFilter(FilterHandler.java:131)

  

11:12:58,328 ERROR [stderr] (default task-88) at org.primefaces.webapp.filter.FileUploadFilter.doFilter(FileUploadFilter.java:111)

  

11:12:58,328 ERROR [stderr] (default task-88) at io.undertow.servlet.core.ManagedFilter.doFilter(ManagedFilter.java:61)

  

11:12:58,328 ERROR [stderr] (default task-88) at io.undertow.servlet.handlers.FilterHandler$FilterChainImpl.doFilter(FilterHandler.java:131)

  

11:12:58,329 ERROR [stderr] (default task-88) at io.undertow.servlet.handlers.FilterHandler.handleRequest(FilterHandler.java:84)

  

11:12:58,329 ERROR [stderr] (default task-88) at io.undertow.servlet.handlers.security.ServletSecurityRoleHandler.handleRequest(ServletSecurityRoleHandler.java:62)

  

11:12:58,329 ERROR [stderr] (default task-88) at io.undertow.servlet.handlers.ServletDispatchingHandler.handleRequest(ServletDispatchingHandler.java:36)

  

11:12:58,329 ERROR [stderr] (default task-88) at org.wildfly.extension.undertow.security.SecurityContextAssociationHandler.handleRequest(SecurityContextAssociationHandler.java:78)

  

11:12:58,329 ERROR [stderr] (default task-88) at io.undertow.server.handlers.PredicateHandler.handleRequest(PredicateHandler.java:43)

  

11:12:58,329 ERROR [stderr] (default task-88) at io.undertow.servlet.handlers.security.SSLInformationAssociationHandler.handleRequest(SSLInformationAssociationHandler.java:131)

  

11:12:58,329 ERROR [stderr] (default task-88) at io.undertow.servlet.handlers.security.ServletAuthenticationCallHandler.handleRequest(ServletAuthenticationCallHandler.java:57)

  

11:12:58,329 ERROR [stderr] (default task-88) at io.undertow.server.handlers.PredicateHandler.handleRequest(PredicateHandler.java:43)

  

11:12:58,329 ERROR [stderr] (default task-88) at io.undertow.security.handlers.AbstractConfidentialityHandler.handleRequest(AbstractConfidentialityHandler.java:46)

  

11:12:58,329 ERROR [stderr] (default task-88) at io.undertow.servlet.handlers.security.ServletConfidentialityConstraintHandler.handleRequest(ServletConfidentialityConstraintHandler.java:64)

  

11:12:58,329 ERROR [stderr] (default task-88) at io.undertow.security.handlers.AuthenticationMechanismsHandler.handleRequest(AuthenticationMechanismsHandler.java:60)

  

11:12:58,329 ERROR [stderr] (default task-88) at io.undertow.servlet.handlers.security.CachedAuthenticatedSessionHandler.handleRequest(CachedAuthenticatedSessionHandler.java:77)

  

11:12:58,329 ERROR [stderr] (default task-88) at io.undertow.security.handlers.NotificationReceiverHandler.handleRequest(NotificationReceiverHandler.java:50)

  

11:12:58,329 ERROR [stderr] (default task-88) at io.undertow.security.handlers.AbstractSecurityContextAssociationHandler.handleRequest(AbstractSecurityContextAssociationHandler.java:43)

  

11:12:58,329 ERROR [stderr] (default task-88) at io.undertow.server.handlers.PredicateHandler.handleRequest(PredicateHandler.java:43)

  

11:12:58,329 ERROR [stderr] (default task-88) at org.wildfly.extension.undertow.security.jacc.JACCContextIdHandler.handleRequest(JACCContextIdHandler.java:61)

  

11:12:58,329 ERROR [stderr] (default task-88) at io.undertow.server.handlers.PredicateHandler.handleRequest(PredicateHandler.java:43)

  

11:12:58,329 ERROR [stderr] (default task-88) at io.undertow.server.handlers.PredicateHandler.handleRequest(PredicateHandler.java:43)

  

11:12:58,329 ERROR [stderr] (default task-88) at io.undertow.servlet.handlers.ServletInitialHandler.handleFirstRequest(ServletInitialHandler.java:285)

  

11:12:58,329 ERROR [stderr] (default task-88) at io.undertow.servlet.handlers.ServletInitialHandler.dispatchRequest(ServletInitialHandler.java:264)

  

11:12:58,330 ERROR [stderr] (default task-88) at io.undertow.servlet.handlers.ServletInitialHandler.access$000(ServletInitialHandler.java:81)

  

11:12:58,330 ERROR [stderr] (default task-88) at io.undertow.servlet.handlers.ServletInitialHandler$1.handleRequest(ServletInitialHandler.java:175)

  

11:12:58,330 ERROR [stderr] (default task-88) at io.undertow.server.Connectors.executeRootHandler(Connectors.java:202)

  

11:12:58,330 ERROR [stderr] (default task-88) at io.undertow.server.HttpServerExchange$1.run(HttpServerExchange.java:792)

  

11:12:58,330 ERROR [stderr] (default task-88) at java.util.concurrent.ThreadPoolExecutor.runWorker(ThreadPoolExecutor.java:1149)

  

11:12:58,330 ERROR [stderr] (default task-88) at java.util.concurrent.ThreadPoolExecutor$Worker.run(ThreadPoolExecutor.java:624)

  

11:12:58,330 ERROR [stderr] (default task-88) at java.lang.Thread.run(Thread.java:748)

  

11:12:58,330 WARNING [ControladorModuloInteligenteMAD] (default task-88) Falha ao consultar o serviço de integração MAD. Erro na conexão. java.net.UnknownHostException: analytics-psim-prod.bbts.com.br