#LLDB-MI Codebase Overview

**MICmdArgContext.h, MICmdArgContext.cpp**
// Details: MI common code class. Command arguments and options string. Holds
//          the context string.
//          Based on the Interpreter pattern.

MICmdArgSet.h, MICmdArgSet.cpp
// Details: MI common code class. Command arguments container class.
//          A command may have one or more arguments of which some may be
//          optional.
//          *this class contains a list of the command's arguments which are
//          validates against the commands argument options string (context
//          string).
//          Each argument tries to extract the value it is looking for.
//          Argument objects added to *this container are owned by this
//          container
//          and are deleted when this container goes out of scope. Allocate
//          argument
//          objects on the heap.
//          It is assumed the arguments to be parsed are read from left to right
//          in
//          order. The order added to *this container is the order they will
//          parsed.

**MICmdArgValBase.h, MICmdArgValBase.cpp**
// Details: MI common code class. Command argument base class. Arguments objects
//          needing specialization derived from *this class. An argument knows
//          what type of argument it is and how it is to interpret the options
//          (context) string to find and validate a matching argument and so
//          extract a value from it.
//          Argument objects are added to the CMICmdArgSet container object.
//          Once added the container they belong to that contain and will be
//          deleted when the container goes out of scope. Allocate argument
//          objects on the heap and pass in to the Add().
//          Note the code is written such that a command will produce an error
//          should it be presented with arguments or options it does not
//          understand.
//          A command can recognise an option or argument then ignore if it
//          wishes (a warning is sent to the MI's Log file). This is so it is
//          hardwired to fail and catch arguments or options that presented by
//          different driver clients.
//          Based on the Interpreter pattern.

**MICmdArgValConsume.h, MICmdArgValConsume.cpp**
// Details: MI common code class. Command argument class. Arguments object
//          needing specialization derived from the CMICmdArgValBase class.
//          An argument knows what type of argument it is and how it is to
//          interpret the options (context) string to find and validate a
//          matching
//          argument. This type having recognised its argument name just
//          consumes
//          that argument or option (ignores it). This is the so the validation
//          process can then ask if all arguments or options have been
//          recognised
//          other an error will occurred "argument not recognised". For example
//          this can be used to consume the "--" text which is not an argument
//          in
//          itself. Normally the GetValue() function (in base class) would
//          return
//          a value for the argument but is not the case for *this argument type
//          object.
//          Based on the Interpreter pattern.

**MICmdArgValFile.h, MICmdArgValFile.cpp**
// Details: MI common code class. Command argument class. Arguments object
//          needing specialization derived from the CMICmdArgValBase class.
//          An argument knows what type of argument it is and how it is to
//          interpret the options (context) string to find and validate a
//          matching
//          argument and so extract a value from it .
//          Based on the Interpreter pattern.

**MICmdArgValListBase.h, MICmdArgValListBase.cpp**
// Details: MI common code class. Command argument with addition options class.
//          For example --recurse 1 2 4 [group ...]. Arguments object that
//          require a list of options associated with them derive from the
//          CMICmdArgValListBase class. Additional options are also extracted
//          from
//          the command arguments text string.
//          An argument knows what type of argument it is and how it is to
//          interpret the options (context) string to find and validate a
//          matching
//          options and so extract a values from it .
//          The CMICmdArgValBase objects are added to the derived argument
//          class's
//          container. The option arguments belong to that derived class and
//          will
//          be deleted that object goes out of scope.
//          Based on the Interpreter pattern.

**MICmdArgValListOfN.h, MICmdArgValListOfN.cpp**
// Details: MI common code class. Command argument class. Arguments object
//          needing specialization derived from the CMICmdArgValBase class.
//          An argument knows what type of argument it is and how it is to
//          interpret the options (context) string to find and validate a
//          matching
//          argument and so extract a value from it .
//          The CMICmdArgValBase objects added to *this ListOfN container belong
//          to this container and will be deleted when *this object goes out of
//          scope.
//          To parse arguments like 'thread-id ...' i.e. 1 10 12 13 ...
//          If vbMandatory argument is true it takes on the (...)+ specification
//          otherwise assumed to be (...)* specification.
//          Based on the Interpreter pattern.

**MICmdArgValNumber.h, MICmdArgValNumber.cpp**
// Details: MI common code class. Command argument class. Arguments object
//          needing specialization derived from the CMICmdArgValBase class.
//          An argument knows what type of argument it is and how it is to
//          interpret the options (context) string to find and validate a
//          matching
//          argument and so extract a value from it .
//          Based on the Interpreter pattern.

**MICmdArgValOptionLong.h, MICmdArgValOptionLong.cpp**
// Details: MI common code class. Command argument class. Arguments object
//          needing specialization derived from the CMICmdArgValBase class.
//          An argument knows what type of argument it is and how it is to
//          interpret the options (context) string to find and validate a
//          matching
//          argument and so extract a value from it.
//          If *this argument has expected options following it the option
//          objects
//          created to hold each of those option's values belong to *this
//          argument
//          object and so are deleted when *this object goes out of scope.
//          Based on the Interpreter pattern.

**MICmdArgValOptionShort.h, MICmdArgValOptionShort.cpp**
// Details: MI common code class. Command argument class. Arguments object
//          needing specialization derived from the CMICmdArgValOptionLong
//          class.
//          An argument knows what type of argument it is and how it is to
//          interpret the options (context) string to find and validate a
//          matching
//          argument and so extract a value from it.
//          If *this argument has expected options following it the option
//          objects
//          created to hold each of those option's values belong to *this
//          argument
//          object and so are deleted when *this object goes out of scope.
//          Based on the Interpreter pattern.

**MICmdArgValPrintValues.h, MICmdArgValPrintValues.cpp**
// Details: MI common code class. Command argument class. Arguments object
//          needing specialization derived from the CMICmdArgValBase class.
//          An argument knows what type of argument it is and how it is to
//          interpret the options (context) string to find and validate a
//          matching
//          argument and so extract a value from it. The print-values looks
//          like:
//            0 or --no-values
//            1 or --all-values
//            2 or --simple-values
//          Based on the Interpreter pattern.

**MICmdArgValString.h, MICmdArgValString.cpp**
// Details: MI common code class. Command argument class. Arguments object
//          needing specialization derived from the CMICmdArgValBase class.
//          An argument knows what type of argument it is and how it is to
//          interpret the options (context) string to find and validate a
//          matching
//          argument and so extract a value from it .
//          Based on the Interpreter pattern.

**MICmdArgValText.h, MICmdArgValText.cpp**
// Details: MI common code class. Command argument class. Arguments object
//          needing specialization derived from the CMICmdArgValBase class.
//          An argument knows what type of argument it is and how it is to
//          interpret the options (context) string to find and validate a
//          matching argument and so extract a value from it.
//
//          Extracts an argument as is removing only surrounding quotes.
//
//          Based on the Interpreter pattern.

**MICmdArgValThreadGrp.h, MICmdArgValThreadGrp.cpp**
// Details: MI common code class. Command argument class. Arguments object
//          needing specialization derived from the CMICmdArgValBase class.
//          An argument knows what type of argument it is and how it is to
//          interpret the options (context) string to find and validate a
//          matching
//          argument and so extract a value from it. Thread group looks like
//          "i1" in the options text.
//          Based on the Interpreter pattern.

**MICmdBase.h, MICmdBase.cpp**
// Details: MI command base class. MI commands derive from this base class.
//          The Command Factory creates command objects and passes them to the
//          Command Invoker. The Invoker takes ownership of any commands created
//          which means it is the only object to delete them when a command is
//          finished working. Commands do not delete themselves.
//          There are two types of command implicitly defined by the state of
//          the m_bWaitForEventFromSBDebugger flag. There is the event type
//          command which registers (command fn) callbacks with the SBListener
//          does some work then wakes up again when called back, does more work
//          perhaps, ends, then the Invoker calls the command's Acknowledge
//          function. The other type of command is one that just does some work,
//          ends, then the Invoker calls the command's Acknowledge function. No
//          events set up.
//          A command's Execute(), Acknowledge() and event callback functions
//          are
//          carried out in the main thread.
//          A command may use the argument derived object classes
//          (CMICmdArgValBase)
//          to factor handling and parsing of different types of arguments
//          presented to a command. A command will produce an error should it
//          be presented with arguments or options it does not understand.

**MICmdCommands.h, MICmdCommands.cpp**
// Overview:    MI command are registered with the MI command factory.
//
//              To implement new MI commands derive a new command class from the
//              command base
//              class. To enable the new command for interpretation add the new
//              command class
//              to the command factory. The files of relevance are:
//                  MICmdCommands.cpp
//                  MICmdBase.h / .cpp
//                  MICmdCmd.h / .cpp

**MICmdCmd.h, MICmdCmd.cpp**
// Overview:    CMICmdCmdEnablePrettyPrinting   implementation.
//              CMICmdCmdSource                 implementation.

**MICmdCmdBreak.h, MICmdCmdBreak.cpp**
// Overview:    CMICmdCmdBreakInsert            implementation.
//              CMICmdCmdBreakDelete            implementation.
//              CMICmdCmdBreakDisable           implementation.
//              CMICmdCmdBreakEnable            implementation.
//              CMICmdCmdBreakAfter             implementation.
//              CMICmdCmdBreakCondition         implementation.

**MICmdCmdData.h, MICmdCmdData.cpp**
// Overview:    CMICmdCmdDataEvaluateExpression     interface.
//              CMICmdCmdDataDisassemble            interface.
//              CMICmdCmdDataReadMemoryBytes        interface.
//              CMICmdCmdDataReadMemory             interface.
//              CMICmdCmdDataListRegisterNames      interface.
//              CMICmdCmdDataListRegisterValues     interface.
//              CMICmdCmdDataListRegisterChanged    interface.
//              CMICmdCmdDataWriteMemoryBytes       interface.
//              CMICmdCmdDataWriteMemory            interface.
//              CMICmdCmdDataInfoLine               interface.
//
//              To implement new MI commands derive a new command class from the
//              command base
//              class. To enable the new command for interpretation add the new
//              command class
//              to the command factory. The files of relevance are:
//                  MICmdCommands.cpp
//                  MICmdBase.h / .cpp
//                  MICmdCmd.h / .cpp
//              For an introduction to adding a new command see
//              CMICmdCmdSupportInfoMiCmdQuery
//              command class as an example.

**MICmdCmdEnviro.h, MICmdCmdEnviro.cpp**
// Overview:    CMICmdCmdEnvironmentCd          interface.
//
//              To implement new MI commands derive a new command class from the
//              command base
//              class. To enable the new command for interpretation add the new
//              command class
//              to the command factory. The files of relevance are:
//                  MICmdCommands.cpp
//                  MICmdBase.h / .cpp
//                  MICmdCmd.h / .cpp
//              For an introduction to adding a new command see
//              CMICmdCmdSupportInfoMiCmdQuery
//              command class as an example.

**MICmdCmdExec.h, MICmdCmdExec.cpp**
// Overview:    CMICmdCmdExecRun                interface.
//              CMICmdCmdExecContinue           interface.
//              CMICmdCmdExecNext               interface.
//              CMICmdCmdExecStep               interface.
//              CMICmdCmdExecNextInstruction    interface.
//              CMICmdCmdExecStepInstruction    interface.
//              CMICmdCmdExecFinish             interface.
//              CMICmdCmdExecInterrupt          interface.
//              CMICmdCmdExecArguments          interface.
//              CMICmdCmdExecAbort              interface.
//
//              To implement new MI commands derive a new command class from the
//              command base
//              class. To enable the new command for interpretation add the new
//              command class
//              to the command factory. The files of relevance are:
//                  MICmdCommands.cpp
//                  MICmdBase.h / .cpp
//                  MICmdCmd.h / .cpp
//              For an introduction to adding a new command see
//              CMICmdCmdSupportInfoMiCmdQuery
//              command class as an example.

**MICmdCmdFile.h, MICmdCmdFile.cpp**
// Overview:    CMICmdCmdFileExecAndSymbols     interface.
//
//              To implement new MI commands derive a new command class from the
//              command base
//              class. To enable the new command for interpretation add the new
//              command class
//              to the command factory. The files of relevance are:
//                  MICmdCommands.cpp
//                  MICmdBase.h / .cpp
//                  MICmdCmd.h / .cpp
//              For an introduction to adding a new command see
//              CMICmdCmdSupportInfoMiCmdQuery
//              command class as an example.

**MICmdCmdGdbInfo.h, MICmdCmdGdbInfo.cpp**
// Overview:    CMICmdCmdGdbInfo    interface.
//
//              To implement new MI commands derive a new command class from the
//              command base
//              class. To enable the new command for interpretation add the new
//              command class
//              to the command factory. The files of relevance are:
//                  MICmdCommands.cpp
//                  MICmdBase.h / .cpp
//                  MICmdCmd.h / .cpp
//              For an introduction to adding a new command see
//              CMICmdCmdSupportInfoMiCmdQuery
//              command class as an example.

**MICmdCmdGdbSet.h, MICmdCmdGdbSet.cpp**
// Overview:    CMICmdCmdGdbSet interface.
//
//              To implement new MI commands, derive a new command class from
//              the command base
//              class. To enable the new command for interpretation add the new
//              command class
//              to the command factory. The files of relevance are:
//                  MICmdCommands.cpp
//                  MICmdBase.h / .cpp
//                  MICmdCmd.h / .cpp
//              For an introduction to adding a new command see
//              CMICmdCmdSupportInfoMiCmdQuery
//              command class as an example.

**MICmdCmdGdbShow.h, MICmdCmdGdbShow.cpp**
// Overview:    CMICmdCmdGdbShow interface.
//
//              To implement new MI commands, derive a new command class from
//              the command base
//              class. To enable the new command for interpretation add the new
//              command class
//              to the command factory. The files of relevance are:
//                  MICmdCommands.cpp
//                  MICmdBase.h / .cpp
//                  MICmdCmd.h / .cpp
//              For an introduction to adding a new command see
//              CMICmdCmdSupportInfoMiCmdQuery
//              command class as an example.

**MICmdCmdGdbThread.h, MICmdCmdGdbThread.cpp**
// Overview:    CMICmdCmdGdbThread      interface.
//
//              To implement new MI commands derive a new command class from the
//              command base
//              class. To enable the new command for interpretation add the new
//              command class
//              to the command factory. The files of relevance are:
//                  MICmdCommands.cpp
//                  MICmdBase.h / .cpp
//                  MICmdCmd.h / .cpp
//              For an introduction to adding a new command see
//              CMICmdCmdSupportInfoMiCmdQuery
//              command class as an example.

**MICmdCmdMiscellanous.h, MICmdCmdMiscellanous.cpp**
// Overview:    CMICmdCmdGdbExit                interface.
//              CMICmdCmdListThreadGroups       interface.
//              CMICmdCmdInterpreterExec        interface.
//              CMICmdCmdInferiorTtySet         interface.
//
//              To implement new MI commands derive a new command class from the
//              command base
//              class. To enable the new command for interpretation add the new
//              command class
//              to the command factory. The files of relevance are:
//                  MICmdCommands.cpp
//                  MICmdBase.h / .cpp
//                  MICmdCmd.h / .cpp
//              For an introduction to adding a new command see
//              CMICmdCmdSupportInfoMiCmdQuery
//              command class as an example.

**MICmdCmdStack.h, MICmdCmdStack.cpp**
// Overview:    CMICmdCmdStackInfoDepth         interface.
//              CMICmdCmdStackInfoFrame         interface.
//              CMICmdCmdStackListFrames        interface.
//              CMICmdCmdStackListArguments     interface.
//              CMICmdCmdStackListLocals        interface.
//              CMICmdCmdStackSelectFrame       interface.
//
//              To implement new MI commands derive a new command class from the
//              command base
//              class. To enable the new command for interpretation add the new
//              command class
//              to the command factory. The files of relevance are:
//                  MICmdCommands.cpp
//                  MICmdBase.h / .cpp
//                  MICmdCmd.h / .cpp
//              For an introduction to adding a new command see
//              CMICmdCmdSupportInfoMiCmdQuery
//              command class as an example.

**MICmdCmdSupportInfo.h, MICmdCmdSupportInfo.cpp**
// Overview:    CMICmdCmdSupportInfoMiCmdQuery          interface.
//
//              To implement new MI commands derive a new command class from the
//              command base
//              class. To enable the new command for interpretation add the new
//              command class
//              to the command factory. The files of relevance are:
//                  MICmdCommands.cpp
//                  MICmdBase.h / .cpp
//                  MICmdCmd.h / .cpp
//              For an introduction to adding a new command see
//              CMICmdCmdSupportInfoMiCmdQuery
//              command class as an example.

**MICmdCmdSupportList.h, MICmdCmdSupportList.cpp**
// Overview:    CMICmdCmdSupportListFeatures            interface.
//
//              To implement new MI commands derive a new command class from the
//              command base
//              class. To enable the new command for interpretation add the new
//              command class
//              to the command factory. The files of relevance are:
//                  MICmdCommands.cpp
//                  MICmdBase.h / .cpp
//                  MICmdCmd.h / .cpp
//              For an introduction to adding a new command see
//              CMICmdCmdSupportInfoMiCmdQuery
//              command class as an example.

**MICmdCmdSymbol.h, MICmdCmdSymbol.cpp**
// Overview:    CMICmdCmdSymbolListLines     interface.
//
//              To implement new MI commands derive a new command class from the
//              command base
//              class. To enable the new command for interpretation add the new
//              command class
//              to the command factory. The files of relevance are:
//                  MICmdCommands.cpp
//                  MICmdBase.h / .cpp
//                  MICmdCmd.h / .cpp
//              For an introduction to adding a new command see
//              CMICmdCmdSupportInfoMiCmdQuery
//              command class as an example.

**MICmdCmdTarget.h, MICmdCmdTarget.cpp**
// Overview:    CMICmdCmdTargetSelect           interface.
//
//              To implement new MI commands derive a new command class from the
//              command base
//              class. To enable the new command for interpretation add the new
//              command class
//              to the command factory. The files of relevance are:
//                  MICmdCommands.cpp
//                  MICmdBase.h / .cpp
//                  MICmdCmd.h / .cpp
//              For an introduction to adding a new command see
//              CMICmdCmdSupportInfoMiCmdQuery
//              command class as an example.

**MICmdCmdThread.h, MICmdCmdThread.cpp**
// Overview:    CMICmdCmdThreadInfo interface.
//
//              To implement new MI commands derive a new command class from the
//              command base
//              class. To enable the new command for interpretation add the new
//              command class
//              to the command factory. The files of relevance are:
//                  MICmdCommands.cpp
//                  MICmdBase.h / .cpp
//                  MICmdCmd.h / .cpp
//              For an introduction to adding a new command see
//              CMICmdCmdSupportInfoMiCmdQuery
//              command class as an example.

**MICmdCmdTrace.h, MICmdCmdTrace.cpp**
// Overview:    CMICmdCmdTraceStatus            interface.
//
//              To implement new MI commands derive a new command class from the
//              command base
//              class. To enable the new command for interpretation add the new
//              command class
//              to the command factory. The files of relevance are:
//                  MICmdCommands.cpp
//                  MICmdBase.h / .cpp
//                  MICmdCmd.h / .cpp
//              For an introduction to adding a new command see
//              CMICmdCmdSupportInfoMiCmdQuery
//              command class as an example.

**MICmdCmdVar.h, MICmdCmdVar.cpp**
// Overview:    CMICmdCmdVarCreate              interface.
//              CMICmdCmdVarUpdate              interface.
//              CMICmdCmdVarDelete              interface.
//              CMICmdCmdVarAssign              interface.
//              CMICmdCmdVarSetFormat           interface.
//              CMICmdCmdVarListChildren        interface.
//              CMICmdCmdVarEvaluateExpression  interface.
//              CMICmdCmdVarInfoPathExpression  interface.
//              CMICmdCmdVarShowAttributes      interface.
//
//              To implement new MI commands derive a new command class from the
//              command base
//              class. To enable the new command for interpretation add the new
//              command class
//              to the command factory. The files of relevance are:
//                  MICmdCommands.cpp
//                  MICmdBase.h / .cpp
//                  MICmdCmd.h / .cpp
//              For an introduction to adding a new command see
//              CMICmdCmdSupportInfoMiCmdQuery
//              command class as an example.

**MICmdData.h, MICmdData.cpp**
// Details: MI command metadata. Holds the command's name, MI number and options
//          as found on stdin. Holds the command's MI output (written to
//          stdout).

**MICmdFactory.h, MICmdFactory.cpp**
// Details: MI Command Factory. Holds a list of registered MI commands that
//          MI application understands to interpret. Creates commands objects.
//          The Command Factory is carried out in the main thread.
//          A singleton class.

**MICmdInterpreter.h, MICmdInterpreter.cpp**
// Details: MI command interpreter. It takes text data from the MI driver
//          (which got it from Stdin singleton) and validate the text to see if
//          matches Machine Interface (MI) format and commands defined in the
//          MI application.
//          A singleton class.

**MICmdInvoker.h, MICmdInvoker.cpp**
// Details: MI Command Invoker. The Invoker works on the command pattern design.
//          There two main jobs; action command Execute() function, followed by
//          the command's Acknowledge() function. When a command has finished
//          its
//          execute function it returns to the invoker. The invoker then calls
//          the
//          command's Acknowledge() function to do more work, form and give
//          back a MI result. In the meantime the Command Monitor is monitoring
//          the each command doing their Execute() function work so they do not
//          exceed a time limit which if it exceeds informs the command(s) to
//          stop work.
//          The work by the Invoker is carried out in the main thread.
//          The Invoker takes ownership of any commands created which means it
//          is the only object to delete them when a command is finished
//          working.
//          A singleton class.

**MICmdMgr.h, MICmdMgr.cpp**
// Details: MI command manager. Oversees command operations, controls command
//          production and the running of commands.
//          Command Invoker, Command Factory and Command Monitor while
//          independent
//          units are overseen/managed by *this manager.
//          A singleton class.

**MICmdMgrSetCmdDeleteCallback.h, MICmdMgrSetCmdDeleteCallback.cpp**
// Details: MI Command Manager interface for client call back.
//          Objects that want to be notified of a command being deleted
//          inherit this interface and register interest in command object
//          deletion. An object deleting a command must not do it itself but
//          call
//          the Command Manager CmdDelete() function to delete a command object.

**MICmnBase.h, MICmnBase.cpp**
// Details: MI common code implementation base class.

**MICmnLLDBBroadcaster.h, MICmnLLDBBroadcaster.cpp**
// Details: MI derived class from LLDB SBBroadcaster API.
//
//          *** This class (files) is a place holder until we know we need it or
//          *** not
//
//          A singleton class.

**MICmnLLDBDebugger.h, MICmnLLDBDebugger.cpp**
// Details: MI proxy/adapter for the LLDB public SBDebugger API. The CMIDriver
//          requires *this object. Command classes make calls on *this object
//          to facilitate their work effort. The instance runs in its own worker
//          thread.
//          A singleton class.

**MICmnLLDBDebuggerHandleEvents.h, MICmnLLDBDebuggerHandleEvents.cpp**
// Details: MI class to take LLDB SBEvent objects, filter them and form
//          MI Out-of-band records from the information inside the event object.
//          These records are then pushed to stdout.
//          A singleton class.

**MICmnLLDBDebugSessionInfo.h, MICmnLLDBDebugSessionInfo.cpp**
// Details: MI debug session object that holds debugging information between
//          instances of MI commands executing their work and producing MI
//          result records. Information/data is set by one or many commands then
//          retrieved by the same or other subsequent commands.
//          It primarily holds LLDB type objects.
//          A singleton class.

**MICmnLLDBDebugSessionInfoVarObj.h, MICmnLLDBDebugSessionInfoVarObj.cpp**
// Details: MI debug session variable object. The static functionality in *this
//          class manages a map container of *these variable objects.

**MICmnLLDBProxySBValue.h, MICmnLLDBProxySBValue.cpp**
// Details: MI proxy wrapper class to lldb::SBValue. The class provides
// functionality
//          to assist in the use of SBValue's particular function usage.

**MICmnLLDBUtilSBValue.h, MICmnLLDBUtilSBValue.cpp**
// Details: Utility helper class to lldb::SBValue. Using a lldb::SBValue extract
//          value object information to help form verbose debug information.

**MICmnLog.h, MICmnLog.cpp**
// Details: MI common code implementation class. Handle application trace
//          activity logging. Medium objects derived from the Medium abstract
///          class are registered with this logger. The function Write is called
//          by a client callee to log information. That information is given to
//          registered relevant mediums. The medium file is registered during
//          *this logs initialization so it will always have a file log for the
//          application.
//          Singleton class.

**MICmnLogMediumFile.h, MICmnLogMediumFile.cpp**
// Details: MI common code implementation class. Logs application fn
// trace/message/
//          error messages to a file. Used as part of the CMICmnLog Logger
//          system. When instantiated *this object is register with the Logger
//          which the Logger when given data to write to registered medium comes
//          *this medium.
//          Singleton class.

**MICmnMIOutOfBandRecord.h, MICmnMIOutOfBandRecord.cpp**
// Details: MI common code MI Out-of-band (Async) Record class. A class that
// encapsulates
//          MI result record data and the forming/format of data added to it.
//          Out-of-band records are used to notify the GDB/MI client of
//          additional
//          changes that have occurred. Those changes can either be a
//          consequence
//          of GDB/MI (e.g., a breakpoint modified) or a result of target
//          activity
//          (e.g., target stopped).
//          The syntax is as follows:
//          "*" type ( "," result )*
//          type ==> running | stopped
//
//          The Out-of-band record can be retrieve at any time *this object is
//          instantiated so unless work is done on *this Out-of-band record then
//          it is
//          possible to return a malformed Out-of-band record. If nothing has
//          been set
//          or added to *this MI Out-of-band record object then text "<Invalid>"
//          will
//          be returned.
//
//          More information see:
//          http://ftp.gnu.org/old-gnu/Manuals/gdb-5.1.1/html_chapter/gdb_22.html//


**MICmnMIResultRecord.h, MICmnMIResultRecord.cpp**
// Details: MI common code MI Result Record class. A class that encapsulates
//          MI result record data and the forming/format of data added to it.
//          The syntax is as follows:
//          result-record ==>  [ token ] "^" result-class ( "," result )* nl
//          token = any sequence of digits
//          * = 0 to many
//          nl = CR | CR_LF
//          result-class ==> "done" | "running" | "connected" | "error" | "exit"
//          result ==> variable "=" value
//          value ==> const | tuple | list
//          const ==> c-string (7 bit iso c string content) i.e. "all" inc
//          quotes
//          tuple ==>  "{}" | "{" result ( "," result )* "}"
//          list ==>  "[]" | "[" value ( "," value )* "]" | "[" result ( ","
//          result )* "]"
//
//          The result record can be retrieve at any time *this object is
//          instantiated so unless work is done on *this result record then it
//          is
//          possible to return a malformed result record. If nothing has been
//          set
//          or added to *this MI result record object then text "<Invalid>" will
//          be returned.
//          More information see:
//          http://ftp.gnu.org/old-gnu/Manuals/gdb-5.1.1/html_chapter/gdb_22.html

**MICmnMIValue.h, MICmnMIValue.cpp**
// Details: MI common code MI Result class. Part of the CMICmnMIValueRecord
//          set of objects.
//          The syntax is as follows:
//          result-record ==>  [ token ] "^" result-class ( "," result )* nl
//          token = any sequence of digits
//          * = 0 to many
//          nl = CR | CR_LF
//          result-class ==> "done" | "running" | "connected" | "error" | "exit"
//          result ==> variable "=" value
//          value ==> const | tuple | list
//          const ==> c-string (7 bit iso c string content)
//          tuple ==>  "{}" | "{" result ( "," result )* "}"
//          list ==>  "[]" | "[" value ( "," value )* "]" | "[" result ( ","
//          result )* "]"
//          More information see:
//          http://ftp.gnu.org/old-gnu/Manuals/gdb-5.1.1/html_chapter/gdb_22.html

**MICmnMIValueConst.h, MICmnMIValueConst.cpp**
// Details: MI common code MI Result class. Part of the CMICmnMIValueConstRecord
//          set of objects.
//          The syntax is as follows:
//          result-record ==>  [ token ] "^" result-class ( "," result )* nl
//          token = any sequence of digits
//          * = 0 to many
//          nl = CR | CR_LF
//          result-class ==> "done" | "running" | "connected" | "error" | "exit"
//          result ==> variable "=" value
//          value ==> const | tuple | list
//          const ==> c-string (7 bit iso c string content)
//          tuple ==>  "{}" | "{" result ( "," result )* "}"
//          list ==>  "[]" | "[" value ( "," value )* "]" | "[" result ( ","
//          result )* "]"
//          More information see:
//          http://ftp.gnu.org/old-gnu/Manuals/gdb-5.1.1/html_chapter/gdb_22.html
//
//          The text formed in *this Result class is stripped of any '\n'
//          characters.

**MICmnMIValueList.h, MICmnMIValueList.cpp**
// Details: MI common code MI Result class. Part of the CMICmnMIValueListRecord
//          set of objects.
//          The syntax is as follows:
//          result-record ==>  [ token ] "^" result-class ( "," result )* nl
//          token = any sequence of digits
//          * = 0 to many
//          nl = CR | CR_LF
//          result-class ==> "done" | "running" | "connected" | "error" | "exit"
//          result ==> variable "=" value
//          value ==> const | tuple | list
//          const ==> c-string (7 bit iso c string content)
//          tuple ==>  "{}" | "{" result ( "," result )* "}"
//          list ==>  "[]" | "[" value ( "," value )* "]" | "[" result ( ","
//          result )* "]"
//          More information see:
//          http://ftp.gnu.org/old-gnu/Manuals/gdb-5.1.1/html_chapter/gdb_22.html

**MICmnMIValueResult.h, MICmnMIValueResult.cpp**
// Details: MI common code MI Result class. Part of the
// CMICmnMIValueResultRecord
//          set of objects.
//          The syntax is as follows:
//          result-record ==>  [ token ] "^" result-class ( "," result )* nl
//          token = any sequence of digits
//          * = 0 to many
//          nl = CR | CR_LF
//          result-class ==> "done" | "running" | "connected" | "error" | "exit"
//          result ==> variable "=" value
//          value ==> const | tuple | list
//          const ==> c-string (7 bit iso c string content)
//          tuple ==>  "{}" | "{" result ( "," result )* "}"
//          list ==>  "[]" | "[" value ( "," value )* "]" | "[" result ( ","
//          result )* "]"
//          More information see:
//          http://ftp.gnu.org/old-gnu/Manuals/gdb-5.1.1/html_chapter/gdb_22.html

**MICmnMIValueTuple.h, MICmnMIValueTuple.cpp**
// Details: MI common code MI Result class. Part of the CMICmnMIValueTupleRecord
//          set of objects.
//          The syntax is as follows:
//          result-record ==>  [ token ] "^" result-class ( "," result )* nl
//          token = any sequence of digits
//          * = 0 to many
//          nl = CR | CR_LF
//          result-class ==> "done" | "running" | "connected" | "error" | "exit"
//          result ==> variable "=" value
//          value ==> const | tuple | list
//          const ==> c-string (7 bit iso c string content)
//          tuple ==>  "{}" | "{" result ( "," result )* "}"
//          list ==>  "[]" | "[" value ( "," value )* "]" | "[" result ( ","
//          result )* "]"
//          More information see:
//          http://ftp.gnu.org/old-gnu/Manuals/gdb-5.1.1/html_chapter/gdb_22.html

**MICmnResources.h, MICmnResources.cpp**
// Details: MI string test data resource definitions. These IDs match up with
//          actual string data in a map internal to CMICmnResources.
//          *** Be sure to update ms_pResourceId2TextData[] array ****

**MICmnStreamStderr.h, MICmnStreamStderr.cpp**
// Details: MI common code class. The MI driver requires this object.
//          CMICmnStreamStderr sets up and tears downs stderr for the driver.
//
//          Singleton class.

**MICmnStreamStdin.h, MICmnStreamStdin.cpp**
// Details: MI common code class. Used to handle stream data from Stdin.
//          Singleton class using the Visitor pattern. A driver using the
//          interface
//          provide can receive callbacks when a new line of data is received.
//          Each line is determined by a carriage return.
//          A singleton class.

**MICmnStreamStdout.h, MICmnStreamStdout.cpp**
// Details: MI common code class. The MI driver requires this object.
//          CMICmnStreamStdout sets up and tears downs stdout for the driver.
//
//          Singleton class.

**MICmnThreadMgrStd.h, MICmnThreadMgrStd.cpp**
// Details: MI's worker thread (active thread) manager.
//          The manager creates threads and behalf of clients. Client are
//          responsible for their threads and can delete them when necessary.
//          This manager will stop and delete all threads on *this manager's
//          shutdown.
//          Singleton class.

**MIDriver.h, MIDriver.cpp**
// Overview:    Defines the entry point for the console application.
//              The MI application (project name MI) runs in two modes:
//              An LLDB native driver mode where it acts no different from the
//              LLDB driver.
//              The other mode is the MI when it finds on the command line
//              the --interpreter option. Command line argument --help on its
//              own will give
//              help for the LLDB driver. If entered with --interpreter then MI
//              help will
//              provided.
//              To implement new MI commands derive a new command class from the
//              command base
//              class. To enable the new command for interpretation add the new
//              command class
//              to the command factory. The files of relevance are:
//                  MICmdCommands.cpp
//                  MICmdBase.h / .cpp
//                  MICmdCmd.h / .cpp


**MIDriverBase.h, MIDriverBase.cpp**
//============================================================================
// Details: MI driver base implementation class. This class has been created so
//          not have to edit the lldb::SBBroadcaster class code. Functionality
//          and attributes need to be common to the LLDB Driver class and the
//          MI Driver class (derived from lldb::SBBroadcaster) so they can call
//          upon each other for functionality fall through and allow the
//          CDriverMgr to manage either (any) driver to be operated on.
//          Each driver instance (the CMIDriver, LLDB::Driver) has its own
//          LLDB::SBDebugger object.
//--

**MIDriverMain.h, MIDriverMain.cpp**
// Overview:    Defines the entry point for the console application.
//              The MI application (project name MI) runs in two modes:
//              An LLDB native driver mode where it acts no different from the
//              LLDB driver.
//              The other mode is the MI when it finds on the command line
//              the --interpreter option. Command line argument --help on its
//              own will give
//              help for the LLDB driver. If entered with --interpreter then MI
//              help will
//              provided.
//              To implement new MI commands derive a new command class from the
//              command base
//              class. To enable the new command for interpretation add the new
//              command class
//              to the command factory. The files of relevance are:
//                  MICmdCommands.cpp
//                  MICmdBase.h / .cpp
//                  MICmdCmd.h / .cpp

**MIDriverMgr.h, MIDriverMgr.cpp**
// Details: MI Driver Manager. Register lldb::SBBroadcaster derived Driver type
//          objects with *this manager. The manager does not own driver objects
//          registered with it and so will not delete when this manager is
//          shutdown. The Driver flagged as "use this one" will be set as
//          current
//          driver and will be the one that is used. Other drivers are not
//          operated. A Driver can call another Driver should it not handle a
//          command.
//          It also initializes other resources as part it's setup such as the
//          Logger and Resources objects (explicit indicate *this object
//          requires
//          those objects (modules/components) to support it's own
//          functionality).
//          The Driver manager is the first object instantiated as part of the
//          MI code base. It is also the first thing to interpret the command
//          line arguments passed to the executable. Bases on options it
//          understands the manage will set up the appropriate driver or give
//          help information. Other options are passed on to the driver chosen
//          to do work.
//          Each driver instance (the CMIDriver, LLDB::Driver) has its own
//          LLDB::SBDebugger.
//          Singleton class.

**MIUtilDateTimeStd.h, MIUtilDateTimeStd.cpp**
// Details: MI common code utility class. Used to retrieve system local date
//          time.

**MIUtilDebug.h, MIUtilDebug.cpp**
// Details: MI debugging aid utility class.

**MIUtilFileStd.h, MIUtilFileStd.cpp**
// Details: MI common code utility class. File handling.

**MIUtilMapIdToVariant.h, MIUtilMapIdToVariant.cpp**
// Details: MI common code utility class. Map type container that hold general
//          object types (by being a variant wrapper)
//          objects by ID.

**MIUtilString.h, MIUtilString.cpp**
// Details: MI common code utility class. Used to help handle text.
//          Derived from std::string

**MIUtilThreadBaseStd.h, MIUtilThreadBaseStd.cpp**
// Details: MI common code utility class. Handle thread mutual exclusion.
//          Embed Mutexes in your Active Object and then use them through Locks.

**MIUtilVariant.h, MIUtilVariant.cpp**
// Details: MI common code utility class. The class implements behaviour of a
//          variant object which holds any data object of type T. A copy of the
//          data object specified is made and stored in *this wrapper. When the
//          *this object is destroyed the data object hold within calls its
//          destructor should it have one.
