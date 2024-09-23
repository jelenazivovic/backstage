## API Report File for "@backstage/plugin-scaffolder-backend"

> Do not edit this file. It is a report generated by [API Extractor](https://api-extractor.com/).

```ts
/// <reference types="node" />

import { ActionContext as ActionContext_2 } from '@backstage/plugin-scaffolder-node';
import { AuthService } from '@backstage/backend-plugin-api';
import { AutocompleteHandler } from '@backstage/plugin-scaffolder-node/alpha';
import * as azure from '@backstage/plugin-scaffolder-backend-module-azure';
import { BackstageCredentials } from '@backstage/backend-plugin-api';
import * as bitbucket from '@backstage/plugin-scaffolder-backend-module-bitbucket';
import * as bitbucketCloud from '@backstage/plugin-scaffolder-backend-module-bitbucket-cloud';
import * as bitbucketServer from '@backstage/plugin-scaffolder-backend-module-bitbucket-server';
import { CatalogApi } from '@backstage/catalog-client';
import { Config } from '@backstage/config';
import { DatabaseService } from '@backstage/backend-plugin-api';
import { DiscoveryService } from '@backstage/backend-plugin-api';
import { Duration } from 'luxon';
import { executeShellCommand as executeShellCommand_2 } from '@backstage/plugin-scaffolder-node';
import { ExecuteShellCommandOptions } from '@backstage/plugin-scaffolder-node';
import express from 'express';
import { fetchContents as fetchContents_2 } from '@backstage/plugin-scaffolder-node';
import * as gerrit from '@backstage/plugin-scaffolder-backend-module-gerrit';
import * as github from '@backstage/plugin-scaffolder-backend-module-github';
import * as gitlab from '@backstage/plugin-scaffolder-backend-module-gitlab';
import { HttpAuthService } from '@backstage/backend-plugin-api';
import { HumanDuration } from '@backstage/types';
import { IdentityApi } from '@backstage/plugin-auth-node';
import { JsonObject } from '@backstage/types';
import { JsonValue } from '@backstage/types';
import { Knex } from 'knex';
import { LifecycleService } from '@backstage/backend-plugin-api';
import { Logger } from 'winston';
import { PermissionEvaluator } from '@backstage/plugin-permission-common';
import { PermissionRule } from '@backstage/plugin-permission-node';
import { PermissionRuleParams } from '@backstage/plugin-permission-common';
import { PermissionsService } from '@backstage/backend-plugin-api';
import { PluginDatabaseManager } from '@backstage/backend-common';
import { RESOURCE_TYPE_SCAFFOLDER_ACTION } from '@backstage/plugin-scaffolder-common/alpha';
import { RESOURCE_TYPE_SCAFFOLDER_TEMPLATE } from '@backstage/plugin-scaffolder-common/alpha';
import { ScaffolderEntitiesProcessor as ScaffolderEntitiesProcessor_2 } from '@backstage/plugin-catalog-backend-module-scaffolder-entity-model';
import { SchedulerService } from '@backstage/backend-plugin-api';
import { Schema } from 'jsonschema';
import { ScmIntegrationRegistry } from '@backstage/integration';
import { ScmIntegrations } from '@backstage/integration';
import { SerializedTask as SerializedTask_2 } from '@backstage/plugin-scaffolder-node';
import { SerializedTaskEvent as SerializedTaskEvent_2 } from '@backstage/plugin-scaffolder-node';
import { TaskBroker as TaskBroker_2 } from '@backstage/plugin-scaffolder-node';
import { TaskBrokerDispatchOptions as TaskBrokerDispatchOptions_2 } from '@backstage/plugin-scaffolder-node';
import { TaskBrokerDispatchResult as TaskBrokerDispatchResult_2 } from '@backstage/plugin-scaffolder-node';
import { TaskCompletionState as TaskCompletionState_2 } from '@backstage/plugin-scaffolder-node';
import { TaskContext as TaskContext_2 } from '@backstage/plugin-scaffolder-node';
import { TaskEventType as TaskEventType_2 } from '@backstage/plugin-scaffolder-node';
import { TaskRecovery } from '@backstage/plugin-scaffolder-common';
import { TaskSecrets as TaskSecrets_2 } from '@backstage/plugin-scaffolder-node';
import { TaskSpec } from '@backstage/plugin-scaffolder-common';
import { TaskSpecV1beta3 } from '@backstage/plugin-scaffolder-common';
import { TaskStatus as TaskStatus_2 } from '@backstage/plugin-scaffolder-node';
import { TemplateAction as TemplateAction_2 } from '@backstage/plugin-scaffolder-node';
import { TemplateActionOptions } from '@backstage/plugin-scaffolder-node';
import { TemplateEntityStepV1beta3 } from '@backstage/plugin-scaffolder-common';
import { TemplateFilter as TemplateFilter_2 } from '@backstage/plugin-scaffolder-node';
import { TemplateGlobal as TemplateGlobal_2 } from '@backstage/plugin-scaffolder-node';
import { TemplateParametersV1beta3 } from '@backstage/plugin-scaffolder-common';
import { UrlReaderService } from '@backstage/backend-plugin-api';
import { WorkspaceProvider } from '@backstage/plugin-scaffolder-node/alpha';
import { ZodType } from 'zod';
import { ZodTypeDef } from 'zod';

// @public @deprecated (undocumented)
export type ActionContext<TInput extends JsonObject> = ActionContext_2<TInput>;

// @public (undocumented)
export type ActionPermissionRuleInput<
  TParams extends PermissionRuleParams = PermissionRuleParams,
> = PermissionRule<
  TemplateEntityStepV1beta3 | TemplateParametersV1beta3,
  {},
  typeof RESOURCE_TYPE_SCAFFOLDER_ACTION,
  TParams
>;

// @public
export const createBuiltinActions: (
  options: CreateBuiltInActionsOptions,
) => TemplateAction_2[];

// @public
export interface CreateBuiltInActionsOptions {
  additionalTemplateFilters?: Record<string, TemplateFilter_2>;
  // (undocumented)
  additionalTemplateGlobals?: Record<string, TemplateGlobal_2>;
  auth?: AuthService;
  catalogClient: CatalogApi;
  config: Config;
  integrations: ScmIntegrations;
  reader: UrlReaderService;
}

// @public
export function createCatalogRegisterAction(options: {
  catalogClient: CatalogApi;
  integrations: ScmIntegrations;
  auth?: AuthService;
}): TemplateAction_2<
  | {
      catalogInfoUrl: string;
      optional?: boolean | undefined;
    }
  | {
      repoContentsUrl: string;
      catalogInfoPath?: string | undefined;
      optional?: boolean | undefined;
    },
  JsonObject
>;

// @public
export function createCatalogWriteAction(): TemplateAction_2<
  {
    entity: Record<string, any>;
    filePath?: string | undefined;
  },
  JsonObject
>;

// @public
export function createDebugLogAction(): TemplateAction_2<
  {
    message?: string | undefined;
    listWorkspace?: boolean | 'with-contents' | 'with-filenames' | undefined;
  },
  JsonObject
>;

// @public
export function createFetchCatalogEntityAction(options: {
  catalogClient: CatalogApi;
  auth?: AuthService;
}): TemplateAction_2<
  {
    optional?: boolean | undefined;
    defaultKind?: string | undefined;
    defaultNamespace?: string | undefined;
    entityRef?: string | undefined;
    entityRefs?: string[] | undefined;
  },
  {
    entities?: any[] | undefined;
    entity?: any;
  }
>;

// @public
export function createFetchPlainAction(options: {
  reader: UrlReaderService;
  integrations: ScmIntegrations;
}): TemplateAction_2<
  {
    url: string;
    targetPath?: string | undefined;
    token?: string | undefined;
  },
  JsonObject
>;

// @public
export function createFetchPlainFileAction(options: {
  reader: UrlReaderService;
  integrations: ScmIntegrations;
}): TemplateAction_2<
  {
    url: string;
    targetPath: string;
    token?: string | undefined;
  },
  JsonObject
>;

// @public
export function createFetchTemplateAction(options: {
  reader: UrlReaderService;
  integrations: ScmIntegrations;
  additionalTemplateFilters?: Record<string, TemplateFilter_2>;
  additionalTemplateGlobals?: Record<string, TemplateGlobal_2>;
}): TemplateAction_2<
  {
    url: string;
    targetPath?: string | undefined;
    values: any;
    templateFileExtension?: string | boolean | undefined;
    copyWithoutRender?: string[] | undefined;
    copyWithoutTemplating?: string[] | undefined;
    cookiecutterCompat?: boolean | undefined;
    replace?: boolean | undefined;
    trimBlocks?: boolean | undefined;
    lstripBlocks?: boolean | undefined;
    token?: string | undefined;
  },
  JsonObject
>;

// @public
export function createFetchTemplateFileAction(options: {
  reader: UrlReaderService;
  integrations: ScmIntegrations;
  additionalTemplateFilters?: Record<string, TemplateFilter_2>;
  additionalTemplateGlobals?: Record<string, TemplateGlobal_2>;
}): TemplateAction_2<
  {
    url: string;
    targetPath: string;
    values: any;
    cookiecutterCompat?: boolean | undefined;
    replace?: boolean | undefined;
    trimBlocks?: boolean | undefined;
    lstripBlocks?: boolean | undefined;
    token?: string | undefined;
  },
  JsonObject
>;

// @public
export const createFilesystemDeleteAction: () => TemplateAction_2<
  {
    files: string[];
  },
  JsonObject
>;

// @public
export const createFilesystemRenameAction: () => TemplateAction_2<
  {
    files: Array<{
      from: string;
      to: string;
      overwrite?: boolean;
    }>;
  },
  JsonObject
>;

// @public @deprecated (undocumented)
export const createGithubActionsDispatchAction: typeof github.createGithubActionsDispatchAction;

// @public @deprecated (undocumented)
export const createGithubDeployKeyAction: typeof github.createGithubDeployKeyAction;

// @public @deprecated (undocumented)
export const createGithubEnvironmentAction: typeof github.createGithubEnvironmentAction;

// @public @deprecated (undocumented)
export const createGithubIssuesLabelAction: typeof github.createGithubIssuesLabelAction;

// @public @deprecated (undocumented)
export type CreateGithubPullRequestActionOptions =
  github.CreateGithubPullRequestActionOptions;

// @public @deprecated (undocumented)
export const createGithubRepoCreateAction: typeof github.createGithubRepoCreateAction;

// @public @deprecated (undocumented)
export const createGithubRepoPushAction: typeof github.createGithubRepoPushAction;

// @public @deprecated (undocumented)
export const createGithubWebhookAction: typeof github.createGithubWebhookAction;

// @public @deprecated (undocumented)
export const createPublishAzureAction: typeof azure.createPublishAzureAction;

// @public @deprecated (undocumented)
export const createPublishBitbucketAction: typeof bitbucket.createPublishBitbucketAction;

// @public @deprecated (undocumented)
export const createPublishBitbucketCloudAction: typeof bitbucketCloud.createPublishBitbucketCloudAction;

// @public @deprecated (undocumented)
export const createPublishBitbucketServerAction: typeof bitbucketServer.createPublishBitbucketServerAction;

// @public @deprecated (undocumented)
export const createPublishBitbucketServerPullRequestAction: typeof bitbucketServer.createPublishBitbucketServerPullRequestAction;

// @public @deprecated (undocumented)
export const createPublishGerritAction: typeof gerrit.createPublishGerritAction;

// @public @deprecated (undocumented)
export const createPublishGerritReviewAction: typeof gerrit.createPublishGerritReviewAction;

// @public @deprecated (undocumented)
export const createPublishGithubAction: typeof github.createPublishGithubAction;

// @public @deprecated (undocumented)
export const createPublishGithubPullRequestAction: (
  options: github.CreateGithubPullRequestActionOptions,
) => TemplateAction_2<
  {
    title: string;
    branchName: string;
    targetBranchName?: string | undefined;
    description: string;
    repoUrl: string;
    draft?: boolean | undefined;
    targetPath?: string | undefined;
    sourcePath?: string | undefined;
    token?: string | undefined;
    reviewers?: string[] | undefined;
    teamReviewers?: string[] | undefined;
    commitMessage?: string | undefined;
    update?: boolean | undefined;
    forceFork?: boolean | undefined;
    gitAuthorName?: string | undefined;
    gitAuthorEmail?: string | undefined;
    forceEmptyGitAuthor?: boolean | undefined;
  },
  JsonObject
>;

// @public @deprecated (undocumented)
export const createPublishGitlabAction: typeof gitlab.createPublishGitlabAction;

// @public @deprecated (undocumented)
export const createPublishGitlabMergeRequestAction: (options: {
  integrations: ScmIntegrationRegistry;
}) => TemplateAction_2<
  {
    repoUrl: string;
    title: string;
    description: string;
    branchName: string;
    targetBranchName?: string | undefined;
    sourcePath?: string | undefined;
    targetPath?: string | undefined;
    token?: string | undefined;
    commitAction?: 'auto' | 'update' | 'delete' | 'create' | undefined;
    projectid?: string | undefined;
    removeSourceBranch?: boolean | undefined;
    assignee?: string | undefined;
  },
  JsonObject
>;

// @public @deprecated
export function createRouter(options: RouterOptions): Promise<express.Router>;

// @public @deprecated (undocumented)
export const createTemplateAction: <
  TInputParams extends JsonObject = JsonObject,
  TOutputParams extends JsonObject = JsonObject,
  TInputSchema extends ZodType<any, ZodTypeDef, any> | Schema = {},
  TOutputSchema extends ZodType<any, ZodTypeDef, any> | Schema = {},
  TActionInput extends JsonObject = TInputSchema extends ZodType<
    any,
    any,
    infer IReturn
  >
    ? IReturn
    : TInputParams,
  TActionOutput extends JsonObject = TOutputSchema extends ZodType<
    any,
    any,
    infer IReturn_1
  >
    ? IReturn_1
    : TOutputParams,
>(
  action: TemplateActionOptions<
    TActionInput,
    TActionOutput,
    TInputSchema,
    TOutputSchema
  >,
) => TemplateAction_2<TActionInput, TActionOutput>;

// @public
export function createWaitAction(options?: {
  maxWaitTime?: Duration | HumanDuration;
}): TemplateAction_2<HumanDuration, JsonObject>;

// @public
export type CreateWorkerOptions = {
  taskBroker: TaskBroker_2;
  actionRegistry: TemplateActionRegistry;
  integrations: ScmIntegrations;
  workingDirectory: string;
  logger: Logger;
  additionalTemplateFilters?: Record<string, TemplateFilter_2>;
  concurrentTasksLimit?: number;
  additionalTemplateGlobals?: Record<string, TemplateGlobal_2>;
  permissions?: PermissionEvaluator;
};

// @public
export interface CurrentClaimedTask {
  createdBy?: string;
  secrets?: TaskSecrets_2;
  spec: TaskSpec;
  state?: JsonObject;
  taskId: string;
  // (undocumented)
  workspace?: Promise<Buffer>;
}

// @public
export class DatabaseTaskStore implements TaskStore {
  // (undocumented)
  cancelTask(
    options: TaskStoreEmitOptions<
      {
        message: string;
      } & JsonObject
    >,
  ): Promise<void>;
  // (undocumented)
  claimTask(): Promise<SerializedTask_2 | undefined>;
  // (undocumented)
  cleanWorkspace({ taskId }: { taskId: string }): Promise<void>;
  // (undocumented)
  completeTask(options: {
    taskId: string;
    status: TaskStatus_2;
    eventBody: JsonObject;
  }): Promise<void>;
  // (undocumented)
  static create(options: DatabaseTaskStoreOptions): Promise<DatabaseTaskStore>;
  // (undocumented)
  createTask(
    options: TaskStoreCreateTaskOptions,
  ): Promise<TaskStoreCreateTaskResult>;
  // (undocumented)
  emitLogEvent(
    options: TaskStoreEmitOptions<
      {
        message: string;
      } & JsonObject
    >,
  ): Promise<void>;
  // (undocumented)
  getTask(taskId: string): Promise<SerializedTask_2>;
  // (undocumented)
  getTaskState({ taskId }: { taskId: string }): Promise<
    | {
        state: JsonObject;
      }
    | undefined
  >;
  // (undocumented)
  heartbeatTask(taskId: string): Promise<void>;
  // (undocumented)
  list(options: {
    createdBy?: string;
    status?: TaskStatus_2;
    filters?: {
      createdBy?: string | string[];
      status?: TaskStatus_2 | TaskStatus_2[];
    };
    pagination?: {
      limit?: number;
      offset?: number;
    };
    order?: {
      order: 'asc' | 'desc';
      field: string;
    }[];
  }): Promise<{
    tasks: SerializedTask_2[];
    totalTasks?: number;
  }>;
  // (undocumented)
  listEvents(options: TaskStoreListEventsOptions): Promise<{
    events: SerializedTaskEvent_2[];
  }>;
  // (undocumented)
  listStaleTasks(options: { timeoutS: number }): Promise<{
    tasks: {
      taskId: string;
      recovery?: TaskRecovery;
    }[];
  }>;
  // (undocumented)
  recoverTasks(options: TaskStoreRecoverTaskOptions): Promise<{
    ids: string[];
  }>;
  // (undocumented)
  rehydrateWorkspace(options: {
    taskId: string;
    targetPath: string;
  }): Promise<void>;
  // (undocumented)
  saveTaskState(options: { taskId: string; state?: JsonObject }): Promise<void>;
  // (undocumented)
  serializeWorkspace(options: { path: string; taskId: string }): Promise<void>;
  // (undocumented)
  shutdownTask(options: TaskStoreShutDownTaskOptions): Promise<void>;
}

// @public
export type DatabaseTaskStoreOptions = {
  database: PluginDatabaseManager | Knex;
};

// @public @deprecated
export const executeShellCommand: typeof executeShellCommand_2;

// @public @deprecated
export const fetchContents: typeof fetchContents_2;

// @public @deprecated
export interface RouterOptions {
  // (undocumented)
  actions?: TemplateAction_2<any, any>[];
  // (undocumented)
  additionalTemplateFilters?: Record<string, TemplateFilter_2>;
  // (undocumented)
  additionalTemplateGlobals?: Record<string, TemplateGlobal_2>;
  // (undocumented)
  additionalWorkspaceProviders?: Record<string, WorkspaceProvider>;
  // (undocumented)
  auth?: AuthService;
  // (undocumented)
  autocompleteHandlers?: Record<string, AutocompleteHandler>;
  // (undocumented)
  catalogClient: CatalogApi;
  concurrentTasksLimit?: number;
  // (undocumented)
  config: Config;
  // (undocumented)
  database: DatabaseService;
  // (undocumented)
  discovery?: DiscoveryService;
  // (undocumented)
  httpAuth?: HttpAuthService;
  // (undocumented)
  identity?: IdentityApi;
  // (undocumented)
  lifecycle?: LifecycleService;
  // (undocumented)
  logger: Logger;
  // (undocumented)
  permissionRules?: Array<
    TemplatePermissionRuleInput | ActionPermissionRuleInput
  >;
  // (undocumented)
  permissions?: PermissionsService;
  // (undocumented)
  reader: UrlReaderService;
  // (undocumented)
  scheduler?: SchedulerService;
  // (undocumented)
  taskBroker?: TaskBroker_2;
  // @deprecated (undocumented)
  taskWorkers?: number;
}

// @public @deprecated
export type RunCommandOptions = ExecuteShellCommandOptions;

// @public @deprecated
export const ScaffolderEntitiesProcessor: typeof ScaffolderEntitiesProcessor_2;

// @public @deprecated
export type SerializedTask = SerializedTask_2;

// @public @deprecated
export type SerializedTaskEvent = SerializedTaskEvent_2;

// @public @deprecated
export type TaskBroker = TaskBroker_2;

// @public @deprecated
export type TaskBrokerDispatchOptions = TaskBrokerDispatchOptions_2;

// @public @deprecated
export type TaskBrokerDispatchResult = TaskBrokerDispatchResult_2;

// @public @deprecated
export type TaskCompletionState = TaskCompletionState_2;

// @public @deprecated
export type TaskContext = TaskContext_2;

// @public @deprecated
export type TaskEventType = TaskEventType_2;

// @public
export class TaskManager implements TaskContext_2 {
  // (undocumented)
  get cancelSignal(): AbortSignal;
  // (undocumented)
  cleanWorkspace?(): Promise<void>;
  // (undocumented)
  complete(result: TaskCompletionState_2, metadata?: JsonObject): Promise<void>;
  // (undocumented)
  static create(
    task: CurrentClaimedTask,
    storage: TaskStore,
    abortSignal: AbortSignal,
    logger: Logger,
    auth?: AuthService,
    config?: Config,
    additionalWorkspaceProviders?: Record<string, WorkspaceProvider>,
  ): TaskManager;
  // (undocumented)
  get createdBy(): string | undefined;
  // (undocumented)
  get done(): boolean;
  // (undocumented)
  emitLog(message: string, logMetadata?: JsonObject): Promise<void>;
  // (undocumented)
  getInitiatorCredentials(): Promise<BackstageCredentials>;
  // (undocumented)
  getTaskState?(): Promise<
    | {
        state?: JsonObject;
      }
    | undefined
  >;
  // (undocumented)
  getWorkspaceName(): Promise<string>;
  // (undocumented)
  rehydrateWorkspace?(options: {
    taskId: string;
    targetPath: string;
  }): Promise<void>;
  // (undocumented)
  get secrets(): TaskSecrets_2 | undefined;
  // (undocumented)
  serializeWorkspace?(options: { path: string }): Promise<void>;
  // (undocumented)
  get spec(): TaskSpecV1beta3;
  // (undocumented)
  updateCheckpoint?(
    options:
      | {
          key: string;
          status: 'success';
          value: JsonValue;
        }
      | {
          key: string;
          status: 'failed';
          reason: string;
        },
  ): Promise<void>;
}

// @public @deprecated (undocumented)
export type TaskSecrets = TaskSecrets_2;

// @public @deprecated
export type TaskStatus = TaskStatus_2;

// @public
export interface TaskStore {
  // (undocumented)
  cancelTask?(options: TaskStoreEmitOptions): Promise<void>;
  // (undocumented)
  claimTask(): Promise<SerializedTask | undefined>;
  // (undocumented)
  cleanWorkspace?({ taskId }: { taskId: string }): Promise<void>;
  // (undocumented)
  completeTask(options: {
    taskId: string;
    status: TaskStatus;
    eventBody: JsonObject;
  }): Promise<void>;
  // (undocumented)
  createTask(
    options: TaskStoreCreateTaskOptions,
  ): Promise<TaskStoreCreateTaskResult>;
  // (undocumented)
  emitLogEvent(options: TaskStoreEmitOptions): Promise<void>;
  // (undocumented)
  getTask(taskId: string): Promise<SerializedTask>;
  // (undocumented)
  getTaskState?({ taskId }: { taskId: string }): Promise<
    | {
        state: JsonObject;
      }
    | undefined
  >;
  // (undocumented)
  heartbeatTask(taskId: string): Promise<void>;
  // (undocumented)
  list?(options: {
    filters?: {
      createdBy?: string | string[];
      status?: TaskStatus | TaskStatus[];
    };
    pagination?: {
      limit?: number;
      offset?: number;
    };
    order?: {
      order: 'asc' | 'desc';
      field: string;
    }[];
  }): Promise<{
    tasks: SerializedTask[];
    totalTasks?: number;
  }>;
  // @deprecated (undocumented)
  list?(options: {
    createdBy?: string;
    status?: TaskStatus;
    filters?: {
      createdBy?: string | string[];
      status?: TaskStatus | TaskStatus[];
    };
    pagination?: {
      limit?: number;
      offset?: number;
    };
    order?: {
      order: 'asc' | 'desc';
      field: string;
    }[];
  }): Promise<{
    tasks: SerializedTask[];
    totalTasks?: number;
  }>;
  // (undocumented)
  listEvents(options: TaskStoreListEventsOptions): Promise<{
    events: SerializedTaskEvent[];
  }>;
  // (undocumented)
  listStaleTasks(options: { timeoutS: number }): Promise<{
    tasks: {
      taskId: string;
    }[];
  }>;
  // (undocumented)
  recoverTasks?(options: TaskStoreRecoverTaskOptions): Promise<{
    ids: string[];
  }>;
  // (undocumented)
  rehydrateWorkspace?(options: {
    taskId: string;
    targetPath: string;
  }): Promise<void>;
  // (undocumented)
  saveTaskState?(options: {
    taskId: string;
    state?: JsonObject;
  }): Promise<void>;
  // (undocumented)
  serializeWorkspace?({
    path,
    taskId,
  }: {
    path: string;
    taskId: string;
  }): Promise<void>;
  // (undocumented)
  shutdownTask?(options: TaskStoreShutDownTaskOptions): Promise<void>;
}

// @public
export type TaskStoreCreateTaskOptions = {
  spec: TaskSpec;
  createdBy?: string;
  secrets?: TaskSecrets_2;
};

// @public
export type TaskStoreCreateTaskResult = {
  taskId: string;
};

// @public
export type TaskStoreEmitOptions<TBody = JsonObject> = {
  taskId: string;
  body: TBody;
};

// @public
export type TaskStoreListEventsOptions = {
  taskId: string;
  after?: number | undefined;
};

// @public
export type TaskStoreRecoverTaskOptions = {
  timeout: HumanDuration;
};

// @public
export type TaskStoreShutDownTaskOptions = {
  taskId: string;
};

// @public
export class TaskWorker {
  // (undocumented)
  static create(options: CreateWorkerOptions): Promise<TaskWorker>;
  // (undocumented)
  protected onReadyToClaimTask(): Promise<void>;
  // (undocumented)
  recoverTasks(): Promise<void>;
  // (undocumented)
  runOneTask(task: TaskContext_2): Promise<void>;
  // (undocumented)
  start(): void;
  // (undocumented)
  stop(): void;
}

// @public @deprecated (undocumented)
export type TemplateAction<TInput extends JsonObject> =
  TemplateAction_2<TInput>;

// @public
export class TemplateActionRegistry {
  // (undocumented)
  get(actionId: string): TemplateAction_2;
  // (undocumented)
  list(): TemplateAction_2[];
  // (undocumented)
  register(action: TemplateAction_2): void;
}

// @public @deprecated (undocumented)
export type TemplateFilter = TemplateFilter_2;

// @public @deprecated (undocumented)
export type TemplateGlobal = TemplateGlobal_2;

// @public (undocumented)
export type TemplatePermissionRuleInput<
  TParams extends PermissionRuleParams = PermissionRuleParams,
> = PermissionRule<
  TemplateEntityStepV1beta3 | TemplateParametersV1beta3,
  {},
  typeof RESOURCE_TYPE_SCAFFOLDER_TEMPLATE,
  TParams
>;

// Warnings were encountered during analysis:
//
// src/deprecated.d.ts:8:1 - (ae-undocumented) Missing documentation for "ActionContext".
// src/deprecated.d.ts:13:22 - (ae-undocumented) Missing documentation for "createTemplateAction".
// src/deprecated.d.ts:18:1 - (ae-undocumented) Missing documentation for "TaskSecrets".
// src/deprecated.d.ts:23:1 - (ae-undocumented) Missing documentation for "TemplateAction".
// src/lib/templating/SecureTemplater.d.ts:6:1 - (ae-undocumented) Missing documentation for "TemplateFilter".
// src/lib/templating/SecureTemplater.d.ts:11:1 - (ae-undocumented) Missing documentation for "TemplateGlobal".
// src/scaffolder/actions/TemplateActionRegistry.d.ts:8:5 - (ae-undocumented) Missing documentation for "register".
// src/scaffolder/actions/TemplateActionRegistry.d.ts:9:5 - (ae-undocumented) Missing documentation for "get".
// src/scaffolder/actions/TemplateActionRegistry.d.ts:10:5 - (ae-undocumented) Missing documentation for "list".
// src/scaffolder/actions/builtin/createBuiltinActions.d.ts:36:5 - (ae-undocumented) Missing documentation for "additionalTemplateGlobals".
// src/scaffolder/actions/deprecated.d.ts:12:22 - (ae-undocumented) Missing documentation for "createGithubActionsDispatchAction".
// src/scaffolder/actions/deprecated.d.ts:17:22 - (ae-undocumented) Missing documentation for "createGithubDeployKeyAction".
// src/scaffolder/actions/deprecated.d.ts:22:22 - (ae-undocumented) Missing documentation for "createGithubEnvironmentAction".
// src/scaffolder/actions/deprecated.d.ts:27:22 - (ae-undocumented) Missing documentation for "createGithubIssuesLabelAction".
// src/scaffolder/actions/deprecated.d.ts:32:1 - (ae-undocumented) Missing documentation for "CreateGithubPullRequestActionOptions".
// src/scaffolder/actions/deprecated.d.ts:37:22 - (ae-undocumented) Missing documentation for "createGithubRepoCreateAction".
// src/scaffolder/actions/deprecated.d.ts:42:22 - (ae-undocumented) Missing documentation for "createGithubRepoPushAction".
// src/scaffolder/actions/deprecated.d.ts:47:22 - (ae-undocumented) Missing documentation for "createGithubWebhookAction".
// src/scaffolder/actions/deprecated.d.ts:52:22 - (ae-undocumented) Missing documentation for "createPublishGithubAction".
// src/scaffolder/actions/deprecated.d.ts:57:22 - (ae-undocumented) Missing documentation for "createPublishGithubPullRequestAction".
// src/scaffolder/actions/deprecated.d.ts:79:22 - (ae-undocumented) Missing documentation for "createPublishBitbucketAction".
// src/scaffolder/actions/deprecated.d.ts:84:22 - (ae-undocumented) Missing documentation for "createPublishBitbucketCloudAction".
// src/scaffolder/actions/deprecated.d.ts:89:22 - (ae-undocumented) Missing documentation for "createPublishBitbucketServerAction".
// src/scaffolder/actions/deprecated.d.ts:94:22 - (ae-undocumented) Missing documentation for "createPublishBitbucketServerPullRequestAction".
// src/scaffolder/actions/deprecated.d.ts:99:22 - (ae-undocumented) Missing documentation for "createPublishAzureAction".
// src/scaffolder/actions/deprecated.d.ts:104:22 - (ae-undocumented) Missing documentation for "createPublishGerritAction".
// src/scaffolder/actions/deprecated.d.ts:109:22 - (ae-undocumented) Missing documentation for "createPublishGerritReviewAction".
// src/scaffolder/actions/deprecated.d.ts:114:22 - (ae-undocumented) Missing documentation for "createPublishGitlabAction".
// src/scaffolder/actions/deprecated.d.ts:119:22 - (ae-undocumented) Missing documentation for "createPublishGitlabMergeRequestAction".
// src/scaffolder/tasks/DatabaseTaskStore.d.ts:41:5 - (ae-undocumented) Missing documentation for "create".
// src/scaffolder/tasks/DatabaseTaskStore.d.ts:48:5 - (ae-undocumented) Missing documentation for "list".
// src/scaffolder/tasks/DatabaseTaskStore.d.ts:67:5 - (ae-undocumented) Missing documentation for "getTask".
// src/scaffolder/tasks/DatabaseTaskStore.d.ts:68:5 - (ae-undocumented) Missing documentation for "createTask".
// src/scaffolder/tasks/DatabaseTaskStore.d.ts:69:5 - (ae-undocumented) Missing documentation for "claimTask".
// src/scaffolder/tasks/DatabaseTaskStore.d.ts:70:5 - (ae-undocumented) Missing documentation for "heartbeatTask".
// src/scaffolder/tasks/DatabaseTaskStore.d.ts:71:5 - (ae-undocumented) Missing documentation for "listStaleTasks".
// src/scaffolder/tasks/DatabaseTaskStore.d.ts:79:5 - (ae-undocumented) Missing documentation for "completeTask".
// src/scaffolder/tasks/DatabaseTaskStore.d.ts:84:5 - (ae-undocumented) Missing documentation for "emitLogEvent".
// src/scaffolder/tasks/DatabaseTaskStore.d.ts:87:5 - (ae-undocumented) Missing documentation for "getTaskState".
// src/scaffolder/tasks/DatabaseTaskStore.d.ts:92:5 - (ae-undocumented) Missing documentation for "saveTaskState".
// src/scaffolder/tasks/DatabaseTaskStore.d.ts:96:5 - (ae-undocumented) Missing documentation for "listEvents".
// src/scaffolder/tasks/DatabaseTaskStore.d.ts:99:5 - (ae-undocumented) Missing documentation for "shutdownTask".
// src/scaffolder/tasks/DatabaseTaskStore.d.ts:100:5 - (ae-undocumented) Missing documentation for "rehydrateWorkspace".
// src/scaffolder/tasks/DatabaseTaskStore.d.ts:104:5 - (ae-undocumented) Missing documentation for "cleanWorkspace".
// src/scaffolder/tasks/DatabaseTaskStore.d.ts:107:5 - (ae-undocumented) Missing documentation for "serializeWorkspace".
// src/scaffolder/tasks/DatabaseTaskStore.d.ts:111:5 - (ae-undocumented) Missing documentation for "cancelTask".
// src/scaffolder/tasks/DatabaseTaskStore.d.ts:114:5 - (ae-undocumented) Missing documentation for "recoverTasks".
// src/scaffolder/tasks/StorageTaskBroker.d.ts:24:5 - (ae-undocumented) Missing documentation for "create".
// src/scaffolder/tasks/StorageTaskBroker.d.ts:26:5 - (ae-undocumented) Missing documentation for "spec".
// src/scaffolder/tasks/StorageTaskBroker.d.ts:27:5 - (ae-undocumented) Missing documentation for "cancelSignal".
// src/scaffolder/tasks/StorageTaskBroker.d.ts:28:5 - (ae-undocumented) Missing documentation for "secrets".
// src/scaffolder/tasks/StorageTaskBroker.d.ts:29:5 - (ae-undocumented) Missing documentation for "createdBy".
// src/scaffolder/tasks/StorageTaskBroker.d.ts:30:5 - (ae-undocumented) Missing documentation for "getWorkspaceName".
// src/scaffolder/tasks/StorageTaskBroker.d.ts:31:5 - (ae-undocumented) Missing documentation for "rehydrateWorkspace".
// src/scaffolder/tasks/StorageTaskBroker.d.ts:35:5 - (ae-undocumented) Missing documentation for "done".
// src/scaffolder/tasks/StorageTaskBroker.d.ts:36:5 - (ae-undocumented) Missing documentation for "emitLog".
// src/scaffolder/tasks/StorageTaskBroker.d.ts:37:5 - (ae-undocumented) Missing documentation for "getTaskState".
// src/scaffolder/tasks/StorageTaskBroker.d.ts:40:5 - (ae-undocumented) Missing documentation for "updateCheckpoint".
// src/scaffolder/tasks/StorageTaskBroker.d.ts:49:5 - (ae-undocumented) Missing documentation for "serializeWorkspace".
// src/scaffolder/tasks/StorageTaskBroker.d.ts:52:5 - (ae-undocumented) Missing documentation for "cleanWorkspace".
// src/scaffolder/tasks/StorageTaskBroker.d.ts:53:5 - (ae-undocumented) Missing documentation for "complete".
// src/scaffolder/tasks/StorageTaskBroker.d.ts:55:5 - (ae-undocumented) Missing documentation for "getInitiatorCredentials".
// src/scaffolder/tasks/StorageTaskBroker.d.ts:83:5 - (ae-undocumented) Missing documentation for "workspace".
// src/scaffolder/tasks/TaskWorker.d.ts:60:5 - (ae-undocumented) Missing documentation for "create".
// src/scaffolder/tasks/TaskWorker.d.ts:61:5 - (ae-undocumented) Missing documentation for "recoverTasks".
// src/scaffolder/tasks/TaskWorker.d.ts:62:5 - (ae-undocumented) Missing documentation for "start".
// src/scaffolder/tasks/TaskWorker.d.ts:63:5 - (ae-undocumented) Missing documentation for "stop".
// src/scaffolder/tasks/TaskWorker.d.ts:64:5 - (ae-undocumented) Missing documentation for "onReadyToClaimTask".
// src/scaffolder/tasks/TaskWorker.d.ts:65:5 - (ae-undocumented) Missing documentation for "runOneTask".
// src/scaffolder/tasks/types.d.ts:123:5 - (ae-undocumented) Missing documentation for "cancelTask".
// src/scaffolder/tasks/types.d.ts:124:5 - (ae-undocumented) Missing documentation for "createTask".
// src/scaffolder/tasks/types.d.ts:125:5 - (ae-undocumented) Missing documentation for "recoverTasks".
// src/scaffolder/tasks/types.d.ts:128:5 - (ae-undocumented) Missing documentation for "getTask".
// src/scaffolder/tasks/types.d.ts:129:5 - (ae-undocumented) Missing documentation for "claimTask".
// src/scaffolder/tasks/types.d.ts:130:5 - (ae-undocumented) Missing documentation for "completeTask".
// src/scaffolder/tasks/types.d.ts:135:5 - (ae-undocumented) Missing documentation for "heartbeatTask".
// src/scaffolder/tasks/types.d.ts:136:5 - (ae-undocumented) Missing documentation for "listStaleTasks".
// src/scaffolder/tasks/types.d.ts:143:5 - (ae-undocumented) Missing documentation for "list".
// src/scaffolder/tasks/types.d.ts:163:5 - (ae-undocumented) Missing documentation for "list".
// src/scaffolder/tasks/types.d.ts:182:5 - (ae-undocumented) Missing documentation for "emitLogEvent".
// src/scaffolder/tasks/types.d.ts:183:5 - (ae-undocumented) Missing documentation for "getTaskState".
// src/scaffolder/tasks/types.d.ts:188:5 - (ae-undocumented) Missing documentation for "saveTaskState".
// src/scaffolder/tasks/types.d.ts:192:5 - (ae-undocumented) Missing documentation for "listEvents".
// src/scaffolder/tasks/types.d.ts:195:5 - (ae-undocumented) Missing documentation for "shutdownTask".
// src/scaffolder/tasks/types.d.ts:196:5 - (ae-undocumented) Missing documentation for "rehydrateWorkspace".
// src/scaffolder/tasks/types.d.ts:200:5 - (ae-undocumented) Missing documentation for "cleanWorkspace".
// src/scaffolder/tasks/types.d.ts:203:5 - (ae-undocumented) Missing documentation for "serializeWorkspace".
// src/service/router.d.ts:17:1 - (ae-undocumented) Missing documentation for "TemplatePermissionRuleInput".
// src/service/router.d.ts:22:1 - (ae-undocumented) Missing documentation for "ActionPermissionRuleInput".
// src/service/router.d.ts:30:5 - (ae-undocumented) Missing documentation for "logger".
// src/service/router.d.ts:31:5 - (ae-undocumented) Missing documentation for "config".
// src/service/router.d.ts:32:5 - (ae-undocumented) Missing documentation for "reader".
// src/service/router.d.ts:33:5 - (ae-undocumented) Missing documentation for "lifecycle".
// src/service/router.d.ts:34:5 - (ae-undocumented) Missing documentation for "database".
// src/service/router.d.ts:35:5 - (ae-undocumented) Missing documentation for "catalogClient".
// src/service/router.d.ts:36:5 - (ae-undocumented) Missing documentation for "scheduler".
// src/service/router.d.ts:37:5 - (ae-undocumented) Missing documentation for "actions".
// src/service/router.d.ts:42:5 - (ae-undocumented) Missing documentation for "taskWorkers".
// src/service/router.d.ts:48:5 - (ae-undocumented) Missing documentation for "taskBroker".
// src/service/router.d.ts:49:5 - (ae-undocumented) Missing documentation for "additionalTemplateFilters".
// src/service/router.d.ts:50:5 - (ae-undocumented) Missing documentation for "additionalTemplateGlobals".
// src/service/router.d.ts:51:5 - (ae-undocumented) Missing documentation for "additionalWorkspaceProviders".
// src/service/router.d.ts:52:5 - (ae-undocumented) Missing documentation for "permissions".
// src/service/router.d.ts:53:5 - (ae-undocumented) Missing documentation for "permissionRules".
// src/service/router.d.ts:54:5 - (ae-undocumented) Missing documentation for "auth".
// src/service/router.d.ts:55:5 - (ae-undocumented) Missing documentation for "httpAuth".
// src/service/router.d.ts:56:5 - (ae-undocumented) Missing documentation for "identity".
// src/service/router.d.ts:57:5 - (ae-undocumented) Missing documentation for "discovery".
// src/service/router.d.ts:58:5 - (ae-undocumented) Missing documentation for "autocompleteHandlers".
```